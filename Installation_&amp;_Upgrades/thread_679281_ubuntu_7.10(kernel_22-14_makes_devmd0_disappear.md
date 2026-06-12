---
title: "ubuntu 7.10(kernel 22-14 makes /dev/md0 disappear"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by vdhagen on 2008-01-26
I tried Servers & Security before, maybe that was not the right place... 

When I did the last upgrade from 6.xx to 7.10 /dev/md0 was not mounted. After the upgrade /dev/md0 had disappeared.

mdadm is installed (newest version)

The mdadm.conf still reads
-- begin listing --
DEVICE /dev/hda1 /dev/hdb1 /dev/hdc1 /dev/hdd1
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f2211e32:3cefb926:62d2bc1f:91ce82a6

MAILADDR root
-- end listing --

Apparently, one problem is that with kernel 2.6.22-14 fdisk -l reports
sda, sbd, sdc, sdd, and sde, where sdb..sde contain the raid partitions.

If I boot ubuntu 7.10 with kernel 2.6.20-16 fdisk -l reports
sda, sbd, sdc, sdd, and sde - but now sda..sdd contain the raid partitions and the /dev/md0 can be mounted and works!

The system disk is an external scsi-disk attached to an adaptec 2940. The other harddisks are internal IDE-disks.

Any idea where to go from here? Just use the old kernel?

Oskar

---

