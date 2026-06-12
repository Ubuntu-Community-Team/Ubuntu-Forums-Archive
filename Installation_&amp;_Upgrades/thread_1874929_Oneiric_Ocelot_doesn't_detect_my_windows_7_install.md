---
title: "Oneiric Ocelot doesn't detect my windows 7 installation"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by bradgy on 2011-11-04
Hi guys and girls

Trying to install 11.10 into what appears to be some unallocated space at the end of my hard disk, however the Live CD doesn't detect my Win7 install for a dual boot. I realise this is probably a partitioning problem and was wondering if someone could take a look at my boot info and tell me if there's a likely culprit to be found there....?

Just a heads up: I was previously trying to install OS X on this system before giving up, wiping the HD with the windows installer, and trying to get ubuntu to work.

Thanks, Brad

  ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   830,420,991   830,214,144   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009230336 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63     7,830,521     7,830,459   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CC765C1B765C091A                       ntfs       System Reserved
/dev/sda2        66F6704EF670210B                       ntfs       
/dev/sdb1        3C0B-0906                              vfat       USB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 08 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  bb 7b 77 00 d1 1d 00 00  00 00 00 00 02 00 00 00  |.{w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 06 09 0b 3c 55  4e 54 49 54 4c 45 44 20  |..)...<UNTITLED |
00000050  31 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |1 FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 
```

---

### Post by bradgy on 2011-11-04
Used Rod Smith's fixparts to get rid of some leftover GPT data. Upon restart the Live CD recognised the windows installation and other file systems.
 
Thanks to the community for this forum and the tools that helped get me up and running :)

---

### Post by mark40 on 2011-11-04
Thank you

Good post

I like your post.

Thats good....

---

