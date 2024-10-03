FROM node:lts-alpine
WORKDIR /app
COPY ./app/package*.json ./
RUN npm ci --only=production
# dirty hack to remove debug logs from library
RUN sed -i 's://if (debug == undefined || debug == false) return;:return;:' node_modules/smarter-devices-promise/src/helper.js
COPY ./app/app.js .
CMD ["node", "app.js"]
