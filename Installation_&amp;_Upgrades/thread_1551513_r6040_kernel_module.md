---
title: "r6040 kernel module"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by admilewis on 2010-08-12
Hi,
I have a norhtec micropc where i'd like to install xubuntu. Norhtec has a vortex CPU x86 compatible and i'm trying to install xubuntu. With my usb pendrive I can boot to install the os. Everything seems goes well but the installation stop when xubuntu try to find the nic. The module interested for this chip is r6040 from RDC semiconductor.
I found this module in a debian kernel image:
[URL="http://packages.debian.org/sid/i386/linux-image-2.6.32-5-686/download"]```
[/URL][http://packages.debian.org/sid/i386/linux-image-2.6.32-5-686/download](http://packages.debian.org/sid/i386/linux-image-2.6.32-5-686/download)
```
and here:
[URL="http://forums.trossenrobotics.com/tutorials/how-to-diy-128/howto-configure-onboard-ethernet-in-ubuntu-904-linux-for-roboard-3278/"]```
[/URL][http://forums.trossenrobotics.com/tutorials/how-to-diy-128/howto-configure-onboard-ethernet-in-ubuntu-904-linux-for-roboard-3278/](http://forums.trossenrobotics.com/tutorials/how-to-diy-128/howto-configure-onboard-ethernet-in-ubuntu-904-linux-for-roboard-3278/)
```

If i try to type "insmod r6040.ko" I got
```

FATAL: error inserting r6040 (...path...) Invalid module format

``` 

because of kernel mismatch version and the same with debian kernel module or the tutorial one.
how could i solve ?
thx very much..

---

