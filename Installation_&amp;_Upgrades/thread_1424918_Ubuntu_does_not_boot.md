---
title: "Ubuntu does not boot"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by ExScientiaVera on 2010-03-08
Hello fellas,

So, I created a new partition (10GB) in my HD in which I installed Ubuntu OS. Unfortunately, afterwards, when I reboot the computer I don't get prompted to choose which OS I want to initialize (Win7 or Ubuntu). Ubuntu does not boot.

Any thoughts as to why? The partition I created has NTFS file system.

Appreciate any help here.

---

### Post by khelben1979 on 2010-03-08
You should not create an Ubuntu partition using NTFS. Go back from the beginning and choose [EXT3]("http://en.wikipedia.org/wiki/Ext3") or [EXT4]("http://en.wikipedia.org/wiki/Ext4") instead.

---

