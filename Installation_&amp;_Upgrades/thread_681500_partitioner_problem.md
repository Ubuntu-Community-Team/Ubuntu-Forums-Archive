---
title: "partitioner problem"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by mckay lee on 2008-01-29
hi 

i try to install dual os, in windows xp i get partitioned (Partition Magic 8.0):
1.linux swap = 2,047.3 MB
2.NTFS (Win XP) = 20,002.8 MB
3.Linux Ext3 = 70,574.6 MB
4.Extended = 60,000.6 MB
5.NTFS (Data Win XP) = 60,000.5 MB

when i try to install ubuntu using bootable cd, 
in the partitioner section it only have one option  manual,
when continue with manual there is no partition available, absolutely empty.
this is weird:confused:.. i have done this in other pc .. there is no problem.
any ideas??

thx

---

### Post by forestpixie on 2008-01-29
from the livecd can you post this from a terminal - apps> accessories
```
sudo fdisk -l
```

there is also a partition editor on the livecd in system> admin I think, if not gparted in a terminal ahould work

---

### Post by mckay lee on 2008-01-29
i have tried gparted but there is no devices detected, 
ubuntu cannot detect the harddisk...
if i go to bios setup the harddisk is not detected as Primary IDE Master but SATA 1,
all ubuntu that i successly installed is on Primary IDE Master.
is that the problem? any solution ?

thx

---

### Post by forestpixie on 2008-01-29
maybe not sure tbh - never had a problem installing to either pata or sata

when you say you'vr tried gparted was that on the livecd or on a gparted livecd - I find the gparted version better, also you could try systemrescue cd - that's got it on too
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

