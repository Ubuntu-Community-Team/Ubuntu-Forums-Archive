---
title: "Ubuntu Studio in VMWare"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Mr.Si on 2011-01-25
Hi all, been trying Ubuntu Studio i386 Alternative iso in WMWare Workstation but when I install it, it auto installs as it auto finds ubuntu and I can't get a graphical interface.

I've tried installing X with Sudo apt-get install xinit

but this has only given me a white console.

Does anyone have any ideas?

Thanks,

Si

---

### Post by Mr.Si on 2011-01-25
Fixed it.

All i needed to do was to type the following:

sudo apt-get install ubuntustudio-desktop

then after a reboot, all worked fine. yay!

---

