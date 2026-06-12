---
title: "Partitioning help."
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by Rillanon on 2010-03-04
Some where along the line, I've made a ext3 file system on a new hard drive but instead of assigning /dev/sdb1, I choosed /dev/sdb which prompted mkfs to ask if I was sure to use the whole device. 

It didn't seem like a problem at the time so I answered yes, I can mount and access all contents on the drive but there is no partition table. 

sudo fdisk -l don't list anything on /dev/sdb... 

Now when I use ext2fsd on windows, the hard drive show up as raw instead of ext3.

Is there anyway around this? Like assigning a "label" so to speak..

---

### Post by johnson.d on 2010-03-05
Windows recognizes the Hard-Disk as unallocated disk, as the partition table is not available. Hence it is not possible to mount the partition in windows.You can probably take backup of the hard-drive in Ubuntu and then re-create the partitions as follows:

1) Create a primary partition which will be /dev/sdb1
2) Create an Extended partition (/dev/sdb2) and create logical drives in the extended partition

You can find help for partitioning from this link:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

