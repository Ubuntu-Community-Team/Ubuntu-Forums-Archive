---
title: "Need to resize boot partition"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by kevdog on 2007-09-07
Im trying to install a new kernel, but my 100 Mb boot partition is full.  When I installed Edgy originally on my 20 Gb Hd, I gave 100mb to /boot, 1Gb to /swap and the rest to the remainder of the file system.  My boot partition is now full and I have about 4 gb free on the remaining main or hda2 partition.  How do I allocate some more to the boot partition without losing data??  No windows is installed.

---

### Post by logos34 on 2007-09-08
Delete the older kernels to free up space or shrink sda2 root partition using gparted live cd (it must be unmounted).

---

### Post by kevdog on 2007-09-08
Cant shrink the hda2 partition -- keeps saying to check partition for errors and if possible fix them.  I did a fsck on the partiion, it said there were no errors, but gparted keeps giving me that DAMN message.  Its really annoying.

---

