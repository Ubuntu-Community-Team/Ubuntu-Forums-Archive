---
title: "Put /home in another partition"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by kuleali on 2005-03-16
I am running warthy and would like to make my /home on another partition.

this is my partition table. 

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdd: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1      237223   119560360+  83  Linux
/dev/hdd2          237224      238216      500472    f  W95 Ext'd (LBA)
/dev/hdd5          237224      238216      500440+  82  Linux swap


How can i do that ?

---

### Post by Xian on 2005-03-16
[QUOTE=kuleali]Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1      237223   119560360+  83  Linux
/dev/hdd2          237224      238216      500472    f  W95 Ext'd (LBA)
/dev/hdd5          237224      238216      500440+  82  Linux swap

How can i do that ?[/QUOTE]
Just create another Linux partition with the size that meets your needs, mount it, copy over your /home contents to that new partition, and then edit your /etc/fstab to load your new /home directory on boot.

Something like this:


/dev/hdd6        /home           reiserfs defaults        0       2

Then delete your old /home directory.

---

### Post by wylfing on 2005-03-16
The problem you are going to run into is that you need to resize your existing partitions to make room for a new one. That is a dicey operation and may very well wipe out all the data on the disk.

There is no 100% safe way around this problem short of backing up your entire disk, repartitioning, reinstalling, and restoring from backups.

However, I am kind of old school about partitions. LVM is still pretty new to me, and that might offer a solution. Are you using LVM? If so, I'd look into how you can move and resize LVM partitions nondestructively. I'd still back up the entire disk first. Messing with partitions is dangerous.

---

### Post by mseney on 2005-03-16
[QUOTE=wylfing]I'd still back up the entire disk first. Messing with partitions is dangerous.[/QUOTE]

**I can't stress the "backup" part enough,  do it NOW.** LOL

---

