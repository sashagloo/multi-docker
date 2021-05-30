# named builder
FROM node:alpine as builder

# unnamed builder
#FROM node:alpine

WORKDIR '/app'
COPY package.json .
RUN npm install --silent
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# use named builder
COPY --from=builder /app/build /usr/share/nginx/html
# use unnamed builder
#COPY --from=0 /app/build /usr/share/nginx/html