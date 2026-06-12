---
title: "Large disk installation issues with 12.04.3"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2013-09-13
Installed Xubuntu 12.04.3 alongside Windows XP SP3 on a 500GB disk, not knowing beforehand of the issues relating to the 4096 byte blocks vs the 512 byte blocks in Windows and fdisk reported that all the drives were "misaligned". I returned to Windows and used the MiniTool Partition Wizard to correct (align) the drives (which meant I had to reinstall Xubuntu.) Now fdisk -l reports the following below. MiniTool indicated that all drives were properly aligned but it's not so according to fdisk. Should I be concerned about Partition 3? I don't even know what "W95 Ext'd (LBA)" means since the drive is NTFS. 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xffb5ffb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   122879999    61438976    7  HPFS/NTFS/exFAT
/dev/sda2       122882048   276475903    76796928    7  HPFS/NTFS/exFAT
/dev/sda3       276479998   976766975   350143489    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       276480000   404475903    63997952    7  HPFS/NTFS/exFAT
/dev/sda6       404477952   532471807    63996928    7  HPFS/NTFS/exFAT
/dev/sda7       532473856   735369215   101447680    7  HPFS/NTFS/exFAT
/dev/sda8       943970304   976766975    16398336   82  Linux swap / Solaris
/dev/sda9       735371264   943962111   104295424   83  Linux

Partition table entries are not in disk order

---

### Post by mastablasta on 2013-09-13
W95 Ext'd (LBA) could be some boot partition or recovery. this is i think FAT32 file format.

---

### Post by ajgreeny on 2013-09-13
"Partition 3 does not start on physical sector boundary." is a relic of times long gone when it did matter about alignment of partitions to sectors.

I am pretty certain you can ignore that error.  See post 2 of [http://forums.linuxmint.com/viewtopic.php?f=190&t=102102&p=579571#p579424](http://forums.linuxmint.com/viewtopic.php?f=190&t=102102&p=579571#p579424)

It would be interesting to see what parted has to say from ```
sudo parted -l
``` and also gdisk ```
sudo gdisk /dev/sda
```the latter of which you will need to install.

I think the W95 Ext'd (LBA) is just a fat32 partition of the type Windows 95 used, though you say it is NTFS; are you sure about that?

---

