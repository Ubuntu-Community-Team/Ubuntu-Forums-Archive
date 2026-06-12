---
title: "Upgrade 15.04 To 15.10 Error"
date: 2016-01-01
forum: Installation &amp; Upgrades
---

### Post by gdawg on 2016-01-01
When upgrading from Ubuntu 15.04 to 15.10 I received the following error; 

Errors were encountered while processing:
 /var/cache/apt/archives/libktploggerprivate8_0.9.0-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help will be appreciated.

uname -r
3.16.0-44-generic

---

### Post by oldos2er on 2016-01-01
Try clearing the cache with ```
sudo apt-get clean
```

---

