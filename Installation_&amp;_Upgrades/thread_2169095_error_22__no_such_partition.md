---
title: "error 22 : no such partition"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by Daniil_Gentili on 2013-08-20
Hello everyone. I've got a problem on my Celsius m440. I've installed ubuntu 12.04 lts on my second partition of my second hard drive (hd1,4) but at the end of the installation my pc couldn't install the loader on the third partition of my second disk and so i selected the place of installation of the loader hd1,4 , the same on witch i have installed ubuntu. i then rebooted and with easybcd added a voice to the boot menu of windows that should lead to the loader. but when i rebooted and selected the voice the boot menu grub gave this error: error 22: no such partition.  i tried to modify the partition but i couldn't.  could any one help me?
thanks.

---

### Post by ajgreeny on 2013-08-20
I think Boot-repair from my signature below may help you; it should certainly help us to figure out what you have done and what partitions etc etc you now have, and where grub has been installed.

---

### Post by Daniil_Gentili on 2013-08-21
thank you so much! it worked!

---

