---
title: "Partition is completely invisible"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by slmnceyhun on 2015-01-22
After I installed Ubuntu 14 to my pc I messed up and lost the MBR of my Win7 installation, in Ubuntu I was able to see my drive and the files inside it (windows, program files etc...) I was looking for a solution and I found this page [http://ubuntuhandbook.org/index.php/2013/08/repair-windows-mbr-from-ubuntu/](http://ubuntuhandbook.org/index.php/2013/08/repair-windows-mbr-from-ubuntu/), I did followed as the page was suggesting and suddenly my partition was lost, im fairly new to ubuntu so sorry if im explaning all this in a verry simple way.

When I type ```
[COLOR=#333333][FONT=Monaco]sudo fdisk -l[/FONT][/COLOR]
``` this is what I get;

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd65287a5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          257040   285282269   142512615    7  HPFS/NTFS/exFAT
/dev/sda2   *   285276160   314570751    14647296   83  Linux
/dev/sda3       314571600   625136399   155282400    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 8283 MB, 8283750400 bytes
28 heads, 44 sectors/track, 13132 cylinders, total 16179200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000552f4


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    16179199     8088576    b  W95 FAT32
```

I installed ```
[COLOR=#333333][FONT=Monaco]sudo apt-get update; sudo apt-get install syslinux[/FONT][/COLOR]
```
than used ```
[COLOR=#333333][FONT=Monaco]sudo dd if=/usr/lib/syslinux/mbr.bin of=[/FONT][/COLOR]**/dev/sda3**
``` (sda3 instead of sda)
After that dint help I tryed with ```
[COLOR=#333333][FONT=Monaco]sudo dd if=/usr/lib/syslinux/mbr.bin of=[/FONT][/COLOR]**/dev/sda**
``` too but that didnt help either.

/dev/sda3 is the partition what I cant reach, not from ubuntu or with win7 recovery. sda1 and sda2 are visible and working correct.

I need to reach the data in sda3 please, if its possible. Thank you.

Edit: Oh and here is the Bootinfo link [http://paste.ubuntu.com/9826710/](http://paste.ubuntu.com/9826710/)

---

### Post by oldfred on 2015-01-22
You never install anything to a NTFS partition boot sector or PBR. That has essential Windows boot info in it.

You may be able to undo it, as it does have a backup PBR, if not you need a Windows repair flash drive to totally rebuild PBR using bootsect.exe.
       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by slmnceyhun on 2015-01-23
Thank you, selecting [Advanced] instead of [Analyse] and selecting [BackupBS] made my partititon visible again, than i fixed my MBR and all was fixed.

---

