---
title: "Installing Ubuntu 13.04 On Samsung arm Chromebook help"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by kirby2ig on 2013-06-10
Okay, so I followed the instructions on this site [http://www.whatthetech.info/installing-ubuntu-13-04-samsung-chromebook/](http://www.whatthetech.info/installing-ubuntu-13-04-samsung-chromebook/) but when it ran the script, it spit out an error. I found out that the file that it was looking to download ([http://cdimage.ubuntu.com/ubuntu-core/daily/current/](http://cdimage.ubuntu.com/ubuntu-core/daily/current/)raring-core-armhf.tar.gz) was replaced with 13.10. Does anyone know where I can get the file?

---

### Post by Xtyn on 2013-06-27
If you modify the script, it will work fine, you should just change:
[http://cdimage.ubuntu.com/ubuntu-core/daily/current/raring-core-armhf.tar.gz](http://cdimage.ubuntu.com/ubuntu-core/daily/current/raring-core-armhf.tar.gz)
to:
[http://cdimage.ubuntu.com/ubuntu-core/releases/13.04/release/ubuntu-core-13.04-core-armhf.tar.gz](http://cdimage.ubuntu.com/ubuntu-core/releases/13.04/release/ubuntu-core-13.04-core-armhf.tar.gz)

---

