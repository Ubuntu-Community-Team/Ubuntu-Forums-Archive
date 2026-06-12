---
title: "xinit: not found"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by secici on 2006-10-17
I instaled xfce4 package to an Ubuntu Server installation.

Give the command startxfce4 but,

An error appeared:

/usr/bin/startxfce4: Starting X server
/usr/bin/startxfce4: line 53: exec: xinit: not found

Thanks for all.

---

### Post by lithod02 on 2006-10-24
If you haven't installed xinit already, then 
sudo apt-get install xinit
and you will probably want the standard X fonts installed.
sudo apt-get install xfonts-base

---

