# firebase_cloud_function_create_custom_token

```jsx
const functions = require("firebase-functions");
const admin = require("firebase-admin");

const serviceAccount = require("./credential-dev.json");

admin.initializeApp({
  credential: admin.credential.cert(serviceAccount),
});

exports.createCustomToken = functions.https.onCall(async (data, context) => {
  const uid = data.uid;
  const token = await admin.auth().createCustomToken(uid);
  return {
    token: token,
  };
});

```
