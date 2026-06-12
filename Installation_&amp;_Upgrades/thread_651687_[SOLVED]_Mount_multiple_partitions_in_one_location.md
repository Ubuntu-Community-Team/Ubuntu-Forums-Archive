---
title: "[SOLVED] Mount multiple partitions in one location"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by oxygen on 2007-12-27
Hi all,

My machine has 3 x 300GB drives with the following partitions:

```

sda1   6GB mounted as /
sda2   2GB mounted as swap
sda3   ~280GB not mounted

sdb1   288GB not mounted

sdc1   288GB not mounted

```

I'm going to use this machine as a samba file server with one share ( /data )

Is it possible to mount sda3, sdb1 and sdc1 in the one folder? When sda3 is full newly created files in /data will go into sdb1 - but it will all look like one samba share to the end user?

Do I need RAID? LVM?


EDIT: Worked out LVM is what to use!

---

