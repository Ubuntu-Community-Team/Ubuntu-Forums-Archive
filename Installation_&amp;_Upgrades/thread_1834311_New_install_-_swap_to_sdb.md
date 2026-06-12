---
title: "New install - /swap to sdb"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by canucksailor on 2011-08-27
Brand new server 11.04 64bit install; problem not covered in Manual (or forum as far as I can find.)

I have a 40Gb SSD that I want to partition as sda with /boot and /root only -- then put /swap (and others) onto RAIDed (mdadm, not necessarily LVM) SATA drives ... (saves too many writes to SSD for longevity.)

Install from .iso on CDrom appears to insist that /swap is on sda.  How do I get around this limit?  Do I have to install /swap to sda, then use gparted?

tnx in advance - paul

---

### Post by dino99 on 2011-08-27
make a manual install using the "alternate" iso, but first prepare your partitions, example of a standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

