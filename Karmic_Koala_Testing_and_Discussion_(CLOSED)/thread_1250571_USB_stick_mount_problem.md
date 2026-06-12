---
title: "USB stick mount problem"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hgergo on 2009-08-26
I have a 4GB hp memory stick and when i insert it the folowing message apare

Error mounting:mount exited with code 1:helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Som solutions

P.S. from ntfs config tool write suport for external drive is enabled

---

### Post by hgergo on 2009-08-27
nobody know the source of the problem?

---

### Post by taavikko on 2009-08-27
> **hgergo said:**
> 

P.S. from ntfs config tool write suport for external drive is enabled

This is obsolete, since ntfs-3g driver is included by default.

Does mounting it manually work?

---

### Post by hgergo on 2009-08-27
from terminal?
can you give me pls the command

---

### Post by taavikko on 2009-08-27
> **hgergo said:**
> from terminal?
can you give me pls the command

There's few ways.
```
devkit-disks --mount /dev/sd*
```
replace * with the actual device and partition example: sdc1

Old washioned way by creating a mount point and then mounting
```
mkdir $HOME/testmount; sudo mount /dev/sd* $HOME/testmount
```
again, replace * with the correct one. The mountpoint can be deleted after you're done testing

---

### Post by hgergo on 2009-08-27
manualy wort with this command mount /dev/sdb1 /media/usbstick (i created firs the usbstick folder).

I have a problem when i giv eject/unmount  and repluging it i must mount it manualy this can be that i mouted it as root?

---

