---
title: "open solaris buid130 + ubuntu 9.10 dual boot howto on acer aspire 1"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by evttxl on 2010-01-02
This worked for me, but YMMV.

1) use gparted and set up the partitions thusly
- sda1, 80G, // for solaris
- sda2, 10G, // for ubuntu
- sda3, 10G, // for google chromium os
- sda4, 50G, // shared ext3 fs

2) install opensolaris
a) boot build 130 livecd, login jack/jack
b) click on the install solaris icon and take all defaults(as far as I remember)

3) install ubuntu 9.10
a) pretty much do what you want but before you click "install"
b) click the advanced tab and tell it to put grub2 on sda2

4) whack solaris' grub to chainload grub2
title Ubuntu 9.10
rootnoverify (hd0,1)
chainloader +1

---

