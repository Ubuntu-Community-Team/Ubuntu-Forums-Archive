---
title: "gparted partition outside disk"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by gladsonvm on 2014-05-06
I cannot install ubuntu. I am geing partiion ouside disk error in gparted. fdisk -l output is as given below
how to fix this?
$fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   117127167    58562560    7  HPFS/NTFS/exFAT
/dev/sda2       117127168   326842424   104857628+   7  HPFS/NTFS/exFAT
/dev/sda3       326842425   649604339   161380957+   7  HPFS/NTFS/exFAT
/dev/sda4       649607175   976784129   163588477+   f  W95 Ext'd (LBA)
/dev/sda5       711049216   833929215    61440000    7  HPFS/NTFS/exFAT
/dev/sda6       833931264   976771071    71419904    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8166 MB, 8166703104 bytes
176 heads, 16 sectors/track, 5664 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095097

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15947520     7972736+   b  W95 FAT32

---

### Post by oldfred on 2014-05-06
Your extended partition ends at a sector beyond the end of drive.

```

 Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR=#ff0000]976773168[/COLOR] sectors


   /dev/sda4 649607175[COLOR=#ff0000] 976784129 [/COLOR]163588477+ f W95 Ext'd (LBA)


```

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by gladsonvm on 2014-05-10
Thanks for the help. I wanted to make the aprtitions show on partition setup screen to install ubuntu. I deleted the first partition as it was not starting from zero and gparted detected partitions.

---

### Post by coffeecat on 2014-05-10
> **gladsonvm said:**
> I deleted the first partition as it was not starting from zero and gparted detected partitions.

The problem was with sda4, not sda1, so whatever you used to delete sda1 must have fixed the partition table sda4 problem. More importantly, the first partition **should** start at sector 2048, not 0. The space between 0 and 2048 is called the embedding area and is important. If you create a new first partition, it will start at sector 2048.

---

### Post by oldfred on 2014-05-10
You also had boot flag on sda1. That means in Windows boot files for all installed versions of Windows are in that one partition. Did you back up boot files?

---

