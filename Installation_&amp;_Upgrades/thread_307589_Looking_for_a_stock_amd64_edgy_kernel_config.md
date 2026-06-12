---
title: "Looking for a stock amd64 edgy kernel config"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by darkshadow on 2006-11-26
I need to upgrade to 2.6.18.3 in order to use my 2GB SD card in my reader but I don't want to completely setup the .config so does someone have it laying around so that I can use it with 2.6.18.3

---

### Post by zgornel on 2006-11-26
The best thing is to get the 2.6.18 (not .3), to patch it with the ck patch and copy the /boot/config-<kernel> as /path-to-kernel-source/.config .

---

### Post by darkshadow on 2006-11-26
Thanks I am downloading the 2.6.18 sources and ck patch right now and am going to try compiling using make-kpkg which I have never used before. If all else fails I will just act like it is my LFS computer.

---

