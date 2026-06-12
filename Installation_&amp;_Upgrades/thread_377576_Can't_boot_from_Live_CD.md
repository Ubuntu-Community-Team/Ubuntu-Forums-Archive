---
title: "Can't boot from Live CD"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by mopok on 2007-03-06
Hi, everyone!
I'm trying to boot Ubuntu 6.06 LTS from Live CD, and the process freezes. After trying to boot into save graphics mode, I've noticed and error in X system. This is someting about this:

VESA(0): No matching modes

Fatal Error: no screens found

I've tried to reconfigure X using dpkg-reconfigure xserver-xorg and selecting vesa driver. The result was the same.

I'm using Celeron 1,7Ghz with 128 RAM and integrated 82845 intel video card.

Actually, I'm trying to install Ubuntu to this machine and if you know, how to do it from console, please, feel free to tell. :)

---

### Post by buuntuu! on 2007-03-06
you would need at least 192MB of RAM to run the live cd!
get the alternate cd, it should install just fine.
consider installing xubuntu, it uses less system resources
have fun!

---

### Post by mopok on 2007-03-07
Thaks! But how and where can I get this alternate CD? And what is the difference between xubuntu and ubuntu?

---

### Post by Kateikyoushi on 2007-03-07
Choose a mirror from here [LINK]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download") then scroll down Under desktop and server will be the alternate cd image.

Ubuntu uses gnome as desktop interface xubuntu uses xfce which requires less resources.

---

