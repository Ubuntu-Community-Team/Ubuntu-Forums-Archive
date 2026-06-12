---
title: "Landscape with OpenID authenticated but not authorised"
date: 2023-05-17
forum: Installation &amp; Upgrades
---

### Post by scahartner on 2023-05-17
We followed the steps described here ([https://ubuntu.com/landscape/docs/external-authentication](https://ubuntu.com/landscape/docs/external-authentication)) to enable authentication against microsoft using the following:

oidc-issuer = [https://login.microsoftonline.com/XXX/v2.0/](https://login.microsoftonline.com/XXX/v2.0/) 
oidc-client-id = XXX 
oidc-client-secret = XXX
oidc-logout-url = [https://login.microsoftonline.com/common/oauth2/v2.0/logout?post_logout_redirect_uri=https://landscape.XXX.com/](https://login.microsoftonline.com/common/oauth2/v2.0/logout?post_logout_redirect_uri=https://landscape.XXX.com/)

This enabled us to log in, however once authenticated the users are not linked to any roles or groups and don't have access. Basically a blank page is presented. 

How can we associate externally authenticated users with roles and groups. 

I have tried to disabled OIDC and using the API to make these users admins, but this didn't work either.

---

### Post by scahartner on 2023-05-18
**Retracted**

---

