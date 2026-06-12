---
title: "Partition not showing up"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Nater43 on 2010-10-17
Ok so I'm having problems trying to install Ubuntu 10.10 onto a partition that I have created. I boot from disc, select that I want to instal it to a partition and when I get to the list of available partitions, it is not listed. Any idea why this is happening?

---

### Post by drpjkurian on 2010-10-17
Hi
Use GParted from the ubuntu live cd and then redo the partition. Moreover the Linux names the partition as sda1 etc.
Please see the tutorials of partitioning by psychocats

---

### Post by sikander3786 on 2010-10-17
Please post the output of

```
sudo fdisk -l
```

from terminal.

---

### Post by Nater43 on 2010-10-17
I ran fdisk -l and this is what I got:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf2b66014

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26          26        4045   42  SFS
/dev/sda4              27       56052   450028845   42  SFS


I then ran gparted and noticed that while my partitions were showing up, all the partition sizes were wrong. sda3, which I have aptly named "Ubuntu" for this install is being listed as 4mb, while under Windows it is listed as 15gb. 

EDIT: Also, when I browse my disk on while on the live cd, the partitions show up just fine, with the correct sizes.

---

### Post by Mark Phelps on 2010-10-17
You have an MS Windows install on this machine?  Or, I should have asked HAD...

When Linux reports SFS for MS Windows machines, that generally means that the Windows machine HDD was formatted using Dynamic Volumes.

If that's what your machine HAD, and you messed with them using GParted, you most likely trashed your machine big-time.

If, however, you did not have an MS Windows install on your machine, then I don't know why GParted is reporting the partitions as SFS.

---

### Post by efflandt on 2010-10-17
Partition type 42 is a Windows specific dynamic partitioning type that Linux may not be fully aware of or feel safe modifying.

**42  Windows 2000 dynamic extended partition marker **If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM). As the Microsoft KnowledgeBase writes: *Pure dynamic disks (those not containing any hard-linked partitions) have only a single partition table entry (type **42**) to define the entire disk. Dynamic disks store their volume configuration in a database located in a 1-MB private region at the end of each dynamic disk.*

---

### Post by Nater43 on 2010-10-17
I have not touched the partitions yet, as I was unsure of what was going on. I've never come across this problem before with partitions. Any way I could fix this under Windows?

---

### Post by srs5694 on 2010-10-18
I've never tried it, but [Partition Wizard's home page](http://www.partitionwizard.com) claims that it supports converting Windows dynamic disks to standard disks without data loss. It could be worth checking out, but I recommend caution. Make backups of all your important data before proceeding.

---

