---
title: "Installation help!?"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by sabobbin on 2007-02-10
I downloaded the IOS file from the site, put it on a CD, and can run ubuntu off the live cd, but when i try to install it onto my computer (on to a 250g external hard drive) i get this error:

"The ext3 file system creation in partition #3 of SCSI3 (0,0,0) (sda) failed."

Any help how to get it to work?

---

### Post by housam on 2007-02-11
Boot from the live CD and in the terminal type : 
```
fdisk -l
```
then post the out come to see the partitions on your HDD.

---

