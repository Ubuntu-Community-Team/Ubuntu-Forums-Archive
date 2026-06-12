---
title: "pb with kdebase update"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by julx on 2007-05-29
hi,

hen trying to install the last update for kdebase (kubuntu feisty) I've got the following error:

```
...
Unpacking replacement kdebase-data ...
dpkg: error processing /var/cache/apt/archives/kdebase-data_4%3a3.5.6-0ubuntu20.1_all.deb (--unpack):
 unable to make backup link of `./usr/share/icons/crystalsvg/64x64/apps/xclock.png' before installing new version: Operation not permitted
...
```

Since I run it with sudo I was a bit surprised, so I had a look that xclock file and it has the following properties:

```
?--sr-xr-- 35646 36791 25939 3.4G 2033-05-15 01:43 xclock.png
```

while all other files in /usr/share/icons/crystalsvg/64x64/apps/ are owned by root and have the rights size and date. What is that?!? I cannot even sudo chown!

Anybody can help?

thanks
julien

---

