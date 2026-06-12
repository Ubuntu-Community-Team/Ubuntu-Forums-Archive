---
title: "Ubuntu 12.10 installation problem"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by hasnain095 on 2013-04-19
[ATTACH=CONFIG]241520[/ATTACH]
 I am a beginner so please explain in plain english. I am trying to install ubuntu 12.10 from a bootable usb. I already have windows 7 installed on my hard drive. The partitioning is as the pic above. When i click install it gives the following error :

The partition /dev/sda5 assigned to / starts at an offset of 2048 bytes from the minimum alignment for this disk, which may lead to very poor performance.

i have read over the forums about this error but i dont understand what they are trying to say. One of them said to try the following command : sudo fdisk -lu

the result are as follows :
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x54c21b8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not start on physical sector boundary.
/dev/sda2   *        2048      206847      102400   42  SFS
/dev/sda3          208845   307403774   153597465    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda4       307406848   976769023   334681088   42  SFS
/dev/sda5          208908    84100274    41945683+  83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6        84100338    88293239     2096451   82  Linux swap / Solaris
Partition 6 does not start on physical sector boundary.
/dev/sda7        88293303   307403774   109555236   83  Linux
Partition 7 does not start on physical sector boundary.

Disk /dev/sdb: 7862 MB, 7862353920 bytes
37 heads, 37 sectors/track, 11217 cylinders, total 15356160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18


```
And i dont understand it...
Any help will be appreciated.

---

### Post by oldfred on 2013-04-19
No, the real issue is the SFS type 42 partitions. That is in Windows dynamic partitions which do not work with Linux. Recently the drivers must have been updated as now it shows and may let you start to install, but grub does not install and you cannot work with the dynamic partitions from Linux. 

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[URL="http://ubuntuforums.org/showthread.php?t=2112005"]http://ubuntuforums.org/showthread.php?t=2112005

[/URL] SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

[URL="http://ubuntuforums.org/showthread.php?t=2112005"]
[/URL]

---

