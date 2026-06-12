---
title: "Screen Resolution"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by palinuxuser on 2006-03-27
Hi, I recently did a fresh install of  Ubuntu 5.10. Everything went fine on the install and updated seemingly fine, but when I am trying to change the default screen resolution, it appears to be locked at 640x480. Any help on this problem would be appreciated, Thanks.

---

### Post by anirban.sam on 2006-03-27
try this from a console, sudo dpkg xserver-xorg

---

### Post by waldorf on 2006-03-27
I believe you can adjust the resolution directly by editing /etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf

then look for the Section entitled "Screen"

---

