FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build
# So the output from that will be the folder inside that
# /app dir called build
# that's where all the production assets gets placed
# So we want to copy that dir over to the nginx phase of our build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html