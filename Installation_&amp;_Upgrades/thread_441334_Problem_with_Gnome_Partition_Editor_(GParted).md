---
title: "Problem with Gnome Partition Editor (GParted)"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2007-05-12
Hi. I Have just resized a NTFS-partition from 280GB to 170GB, make an ext3-partion, shuffeld data to the ext3-partion, resized the NTFS-partition to 70GB.  Now i have one 70GB NTFS-partition, 100GB unallocated area and 110GB Ext3 partition. The unallocated area is between NTFS-partition and the Ext3-partition, and my intention was to make the Ext3 partition bigger and use the unallocated area.  But I can't do that!  I can only get the Ext3 partition lesser :( . I made an primary Ext3 partion. 

Please help.

---

### Post by orrorin on 2007-05-12
I believe you can move partitions in Windows Disk Manager; never tried it though. Don't remember seeing that option in GParted.

---

### Post by Azyx on 2007-05-12
There is a chose Resize/Move partition, but when a select that, i only can make it lesser, not bigger or move it. I dont have windows anymore.
/Azyx

---

### Post by Azyx on 2007-05-12
I downloaded GParted-liveCD [http://gparted.sourceforge.org](http://gparted.sourceforge.org) and i worked fine :) Must be some bug in the version in Ubuntu or that i mounted the partition strange in Ubuntu.

---

### Post by Azyx on 2007-05-12
I don't think you can that. Especially not Ext3 or other partion except FAT and NTFS,  GParted are more like Partition Magic, and why do a lot of Windowspeople bye Partition magic, if you can do it in windows?

> **orrorin said:**
> I believe you can move partitions in Windows Disk Manager; never tried it though. Don't remember seeing that option in GParted.

---

