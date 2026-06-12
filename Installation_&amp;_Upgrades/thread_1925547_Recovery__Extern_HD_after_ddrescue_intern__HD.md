---
title: "Recovery  Extern HD after ddrescue intern  HD"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by fdpci on 2012-02-14
Hello,
I damage my USB extern iomega hd using ddrescue.
Hd intern=sda           Hd extern=sdb(ntfs)
COMAND:    ddrescue /dev/sda /dev/sdb
When I saw during the firts seconds that ddrescue was copying directly to the extern sdb without creating a image file (the tutorial wasn't clear!) I stoped with control c
But now, the external HD nfts reproducer can'not find the files in sdb.
How can I restore the extern hd sdb to the state before using ddrescue?
Thanks.

---

### Post by darkod on 2012-02-14
What is "ntfs reproducer"?

If you run:
sudo fdisk -l

does it list the disk ok?

---

### Post by fdpci on 2012-02-15
ntfs reproducer: Iomega  Sreen Player lay Plus  1TB HD Media
bad operation ddrescue: ddrescue 250gb fat > HD iomega  sdb4 ntfs (I let 20 seconds stop with control c}

results fdisk -l  : Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x839f6035

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              10          74      522112+  83  Linux
/dev/sdb2              75         106      257040   83  Linux
/dev/sdb3             107         171      522112+  82  Linux swap / Solaris
/dev/sdb4             172      121598   975362377+   7  HPFS/NTFS
...........................................................................................................................
root@ubuntu:/home/ubuntu# fdisk /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').
........................................................................................................................................
Command (m for help): p

Disk /dev/sdb4: 998.8 GB, 998771074560 bytes
255 heads, 63 sectors/track, 121427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4cd800d0

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb4p1               1       30401   244196001    b  W95 FAT32
..................................................................................................................................
Command (m for help): v
Remaining 1462332752 unallocated 512-byte sectors

---

### Post by fdpci on 2012-02-15
...................................................................................................................................
results of test drive:
Partition table type (auto): Intel
Disk /dev/sdb - 1000 GB / 931 GiB - ST310005 28AS
Partition table type: Intel

Analyse Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 82
check_part_i386 failed for partition type 07
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 P Linux                     9   0  1    73 254 63    1044225
 2 P Linux                   74   0  1   105 254 63     514080
 3 P Linux Swap             106   0  1   170 254 63    1044225
 3 P Linux Swap             106   0  1   170 254 63    1044225
Invalid NTFS or EXFAT boot
 4 P HPFS - NTFS            171   0  1 121597 254 63 1950724755
 4 P HPFS - NTFS            171   0  1 121597 254 63 1950724755
***********************************************************************************************
How can I fix the sdb4 partition and the size to restore the original ntfs 998.8 GB  ?

---

### Post by darkod on 2012-02-15
Looks like you overwrote the partition table.

Not sure if you can recover this, but you could try with testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Do a deeper search and see if the original partition is found, if you know what it looked like. The point is that these disks sometimes do have some linux partition on them from factory, that's how they work. Can you tell a difference between the original partitions and the partitions that started to be copied with dd?

Do the deep search and take a good look at the partitions found. Post the results if you are not sure.

---

