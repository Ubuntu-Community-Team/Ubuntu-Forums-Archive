---
title: "HowTo: 64-bit Google Desktop Search"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-09-05
I've just successfully installed Google Desktop Search on Gutsy Tribe-5 64-bit. Google only provide 32-bit binaries so if you follow the suggested installation method it will fail, reporting wrong architecture type.

[Download Desktop for Linux](http://desktop.google.com/en/linux/install.html?dl=deb) deb and save it to disk.
```
$ sudo apt-get install ia32-libs ia32-libs-gtk
$ sudo dpkg --force-all -i google-desktop-linux_current_i386.deb
$ gdlinux

```
The last command will start Google Desktop search and install an icon in the notification area. You can right-click that to access the menu and configuration options.

---

### Post by kr0n1x on 2007-11-04
it works thanks :)

---

### Post by jacrider on 2007-11-22
Thanks!  I love Google Desktop and have recently upgraded to Gutsy in 64 bit.

---

### Post by amberhong on 2007-12-24
Google desktop linux 64bit is available now!:)

---

