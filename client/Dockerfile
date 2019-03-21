#Specify a base image
FROM node:alpine as builder

WORKDIR '/app'

#Install some dependencies
COPY ./package.json ./
RUN npm install
COPY . .

#Default startup command
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html 