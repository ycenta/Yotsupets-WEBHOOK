# Sample Code for Twitch EventSub Webhooks using NodeJS

### Set .env file
Create a .env file with the following variables

```
TWITCH_CLIENT_ID=
TWITCH_ACCESS_TOKEN=
NGROK_TUNNEL_URL=
#webhook url()
```

### Start the Server
```
docker build . -t ycenta/webhook-twitch-node
docker run -p 3000:3000 -d ycenta/webhook-twitch-node

docker logs <container_id>
docker kill <container_id>
```

## Webhook Subscription Creation
Once the server is up and running you can send a POST to `http://localhost:3000/createWebhook/<twitchID>` to create a new *channel.follow* webhook. 

You can modify the *createWebHookBody* payload in the index.js to try out other webhooks as well.

## Handling Notifications
The `app.post('/notification',...)` function will handle all notifications sent to your callback URL. It will reply to Twitch with the proper responses to complete the webhook flows succesfuly plus logging payloads to the console.
