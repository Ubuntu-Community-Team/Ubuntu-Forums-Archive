---
title: "Lubuntu 12.04 install Broadcom wireless AWOL, Acer  Aspire"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by casbahdk on 2012-07-24
I am unable to get the Broadcom wireless (Broadcom BCM43228 [14e4:4359]) running in connection with a Lubuntu 12.04 install on my Acer Aspire One 725```
$ lspci
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
``````
/var/log/jockey.log
2012-07-24 21:06:46,888 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
```

---

### Post by casbahdk on 2012-07-25
It looks like this was solved with the latest update.

---

