---
title: "Deleted GPG Keys"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by sarath_it on 2007-08-16
I was getting some NOT AUTHENTICATED errors while auto-update. so i deleted all keys :( my bad.. i added tux family keys and the fonts keys, but i could not find how to get the keys for original ubuntu dists. 

what i do apt-get update, i get the following 

```
W: GPG error: http://security.ubuntu.com feisty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com feisty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
```

Please help

---

### Post by Seisen on 2007-08-16
If you go to System>Administration.Software Sources their should be a box that says revert and it will revert it back to the defaults, see if that works.

---

### Post by sarath_it on 2007-08-16
coool.. works now ;)

---

