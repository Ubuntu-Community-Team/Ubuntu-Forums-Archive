---
title: "Upgraded to 22.04, Online Accounts signing cert authority not known?"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by benkhoo on 2022-08-13
hi

I upgraded to 22.04 today and while largely, everything worked, my "Online Accounts" seems to have issues.
Particularly, my server accounts keeps getting a "Signing certificate authority is not known".
The online account is connecting to my own Nextcloud server and is providing connections with a SSL cert from "LetsEncrypt".
This was working in 20.04. Nextcloud desktop is also working fine.
Connecting to my nextcloud instance over a browser also shows that the cert is definitely trusted and not expired.

I have tired re-downloading the root certs from letsencrypt and refreshing the cert store but it doesn't seem to help.
Does anyone have any idea what i might need to check or do to re-enable to connection?

Thanks lots for any help anyone can render!

---

