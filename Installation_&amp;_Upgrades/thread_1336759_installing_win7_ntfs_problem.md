---
title: "installing win7? ntfs problem"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by blinkblink on 2009-11-24
can someone tell me how to install win7? not dualboot, but to purge ubuntu and use win7 as primary OS. I run into a problem right now when I try to clean install from cd boot because the disk is not in NTFS format, so win7 can't be installed. What to do?

---

### Post by Some Penguin on 2009-11-25
Seems to me that you should be able to boot just about any installer or 'rescue' live CD (anything that has an fdisk), access the shell, and use fdisk to delete the Ubuntu partitions.  I don't know if you have to *create* an NTFS partition yourself (create the partition, mark it NTFS, then initialize the filesystem with mkntfs -- which might be harder to find on live CDs) or if the W7 installer will do it for you.

---

### Post by wilee-nilee on 2009-11-25
How are you trying to install W7? if it is a DVD then it will overwrite whatever is on there, no matter what type of partition you have.

---

