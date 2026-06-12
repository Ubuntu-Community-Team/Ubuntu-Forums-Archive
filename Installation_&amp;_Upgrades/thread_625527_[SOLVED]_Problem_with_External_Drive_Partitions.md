---
title: "[SOLVED] Problem with External Drive Partitions"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by nsilva on 2007-11-28
Hello there,

I bought a new External Harddrive for storage mainly (500GB). It came with FAT 32 out of the box, within an XP Box I re-format it to NTFS, and have been using it since with ubuntu.

Since I manage large files in the drive (MythTv :)), I have been wanting to change the FS to RaiserFS. I was able to resize the NTFS partition by using the ntfstools
[http://www.nishants.net/articles/ntfsresize.htm](http://www.nishants.net/articles/ntfsresize.htm). I resized to 50GB, theoretically leaving 450GB unallocated.

I ran into the following problems to create RaiserFs in the unallocated space,

```
sudo fdisk /dev/sdb1
```

```
Command (m for help): p

Disk /dev/sdb1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I dont understand the result from the table, neither I'm able to see which one is the NTFS partition, and which ones can I delete.

I also tried using Gparted; however, it tells me the whole disk is unallocated, is not able to read any partitions.

Some Advice to create a RaiserFS would be appreciated it. I have no means of wipping the whole disk, since I have no space for those 50GB of NTFS, just a heads up.

---

### Post by nsilva on 2007-11-28
I solved it myself, I was doing

```
fdisk /dev/sdb1
``` 

instead of 


```
fdisk /dev/sdb
``` 

duh =)

---

