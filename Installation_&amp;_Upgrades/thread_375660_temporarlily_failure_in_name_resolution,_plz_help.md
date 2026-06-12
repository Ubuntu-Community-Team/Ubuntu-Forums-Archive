---
title: "temporarlily failure in name resolution, plz help"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by netbug on 2007-03-04
i am newbie for ubuntu

i try to install and it goes well
and order to put out the installation cd in order to boot from Hard disk

when it boots there is one part error

it say temporarily failure in name resolution and after that it can not loading and become black screen.

any one can tell me what should i do

thanx for your help


my cpu spec

p4 intel 2.4
vga Nvdia MX 400 4x 64 MB
DDR 256 MB
Monitor 14 "

---

### Post by zvacet on 2007-03-04
Ctrl+alt+F1 and you will be in terminal
```
sudo dpkg-reconfigure xserver-xorg
```

---

