---
title: "[boot-repair] summary report. help please"
date: 2016-12-10
forum: Installation &amp; Upgrades
---

### Post by btforsythe2 on 2016-12-10
Here's the report: [http://paste2.org/KFfH9zXx](http://paste2.org/KFfH9zXx)

---

### Post by oldfred on 2016-12-10
So what is problem.

I do not see partitions with the labels you are trying to mount in fstab.

I do not understand why Boot-Repair would even try to install grub to sdb, as that is your live installer? May be better to just use advanced mode and choose install and sda.

Never seen this error before, but few use labels.
> grub-install: warning: Attempting to install GRUB to a disk with multiple partition labels.  This is not supported yet..

grub-install: error: embedding is not possible, but this is required for cross-disk install.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:1



---

