---
title: "howto: copy bigger partition to smaller one using tar image"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by lptr on 2007-02-26
Howto copy one partition with say 8 GByte used space and 100 GByte free to another one that has just 20 GByte size?

It is necessary to store data in 2 GByte file chunks so that it can be transfered to external CD/DVDs. The very old Norton Ghost was able to provide that kind of image creation/restore on VFat drives.

Partimage is not able to achieve this. It segfaults with message: Target partition to small. Ghost for Unix G4U seems to have similar problems.

Opposed to partimage it was not possible for me to get kdar installed on live-CD started system 6.10 (some broken? package problems - we saw this some weeks ago here on list). 

How I can achieve to create something like a split image file using normal tar. I searched for this (man/google/forums) but could not get it working, yet.

This is the idea behind:
```
# mkdir /OLD
# mkdir /NEW
# mount -t ext3 /dev/hda1 /OLD
# mount -t ext3 /dev/sda1 /NEW
# cd /OLD
# tar -cSp --numeric-owner -f - . | ( cd /NEW && tar xSpvf - )

```
Any help would be highly appreciated.

rob*

---

