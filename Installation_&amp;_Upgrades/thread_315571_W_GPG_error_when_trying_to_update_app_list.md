---
title: "W: GPG error when trying to update app list"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by meshica7 on 2006-12-09
Hey folks!
 When I recently tried to update my  my list of applications (under the  Add/Remove app),I recieved the following error:

[COLOR="Blue"]**W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718**[/COLOR]

 I have no clue how to fix this.Any hints/suggestions?

 Thanx!
 Juan

---

### Post by ThrobbingBrain66 on 2006-12-09
open a terminal and use this compound command to get the key, replacing the x's with the last 8 digits of that long number ( 12B83718 )

```
gpg --keyserver subkeys.pgp.net --recv xxxxxxxx && gpg --export --armor xxxxxxxx | apt-key add -
```

---

