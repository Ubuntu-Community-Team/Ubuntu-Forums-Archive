---
title: "Overlapping partitions can't install ubuntu"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by dink123 on 2014-08-21
Hi, when I try to install ubuntu it doesn't detect the windows OS and doesn't show up harddisk partitions as well. I think the issue is due to partition overlapping. 
Here is the output of fdisk. How do I fix it?

sudo fdisk -lu /dev/sda

```

 Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xde15f6b0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   219014144   109403648+   7  HPFS/NTFS/exFAT
/dev/sda3       259971072   628623449   184326189    7  HPFS/NTFS/exFAT
/dev/sda4       628609024   976768064   174079520+   f  W95 Ext'd (LBA)
/dev/sda5       628611072   751504634    61446781+   7  HPFS/NTFS/exFAT
 
```

---

### Post by TheFu on 2014-08-21
You have a tough decision to make.  Appears the system has already used all 4 primary partitions and Ubuntu needs 2.

I can't tell from the table above (don't feel like doing hte math) - but shrink sda5, and add 15G for sda6 and 2G for sda7 - leave them empty.  During the Ubuntu install - when it comes to disk questions - "do something else" is the choice you want.  Then put / on sda6 and make sda7 "linux swap".  It will work.

Oh - and please, please, please use "**code tags**" when posting command output here - much easier to read.

fdisk may be incorrect on GPT disks. Use **parted** going forward until the fixed fdisks are part of every distro installed. It is correct here, so don't worry.

---

### Post by oldfred on 2014-08-21
/dev/sda3       259971072   6286[COLOR=#ff0000]23449[/COLOR]   184326189    7  HPFS/NTFS/exFAT
/dev/sda4       6286[COLOR=#ff0000]09024[/COLOR]   976768064   174079520+   f  W95 Ext'd (LBA)

Your sda4 starts before the end of sda3. (and sda5 inside sda4 also starts before the end of sda3.
Best case you have not written any data at the end of sda3, but with ext4 it is possible. 

Make sure you have good backups.
And you will need to shrink sda3 to one or two sectors less than the start of sda4.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

Save that file to external disk.
But sfdisk is is not like the fdisk output which has start & end. sfdisk has start an size, so some math is required.

A few posts from those who really know partitions.

 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

