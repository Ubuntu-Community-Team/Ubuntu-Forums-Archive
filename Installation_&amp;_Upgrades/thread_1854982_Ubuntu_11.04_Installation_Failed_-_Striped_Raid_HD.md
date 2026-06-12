---
title: "Ubuntu 11.04 Installation Failed - Striped Raid HDD Issue"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by Grimlin on 2011-10-05
I have a new desktop with no operating system. I have tried to install several linux distros, and have had similar installation issues. All relating to grub/ boot-loader issues.

Im currently working off the ubuntu 11.04 live cd iso. 

In Short: (After many changes to the installation process, and many failed attempts)

I have 2 hard drives that wont install ubuntu when set to RAID in Bios.
If I set the HDD to IDE instead of RAID, the installer picks up only 1 TB HDD; yet I can see  2x 500GB in the bootup process. 
With IDE set the instalation completes but wont boot.
When trying to fix the boot record from the live cd, the boot-repair program gets stuck enabling striped array.

Any suggestions on how to fix the current installation that wont boot, or how to set up a new installation based on my striped array on or off, which ever works, would be greatly appreciated!!!

[B]My system:
[/B]
Intel Core i5 2400 Processor, 6MB, 3.1GHz


                  2 X 2GB DDR3 1333Mhz Memory Speed : 2 X 1333Mhz


 
2 X 500GB 6Gb/s Hard Drive Interface : 2 X SATA


 
NVIDIA GeForce GT 430 1024MB Graphics Card


Intel H67 Chipset Motherboard


[B]ubuntu@ubuntu:~$ sudo fdisk -lu
[/B]
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x0003 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e8fee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             512      976383      487936   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          976894  1953534975   976279041    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       649979912  4509198346  1929609217+   1  FAT12

Disk /dev/dm-0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x000e8fee

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1             512      976383      487936   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2          976894  1953534975   976279041    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/dm-0p5          976896    10741759     4882432   82  Linux swap / Solaris
/dev/dm-0p6        10742272    30273023     9765376   83  Linux
/dev/dm-0p7        30273536  1953534975   961630720   83  Linux

Disk /dev/dm-1: 499 MB, 499646464 bytes
255 heads, 63 sectors/track, 60 cylinders, total 975872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-3: 4999 MB, 4999610368 bytes
255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-4: 9999 MB, 9999745024 bytes
255 heads, 63 sectors/track, 1215 cylinders, total 19530752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-4 doesn't contain a valid partition table

Disk /dev/dm-5: 984.7 GB, 984709857280 bytes
255 heads, 63 sectors/track, 119717 cylinders, total 1923261440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-5 doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

 
**sudo bash ~/Desktop/boot_info_script*.sh**
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of 
    /dev/mapper/isw_bheiihfbii_Volume0.

isw_bheiihfbii_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

isw_bheiihfbii_Volume02: _______________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bheiihfbii_Volume05: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bheiihfbii_Volume06: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bheiihfbii_Volume07: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: isw_bheiihfbii_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_bheiihfbii_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bheiihfbii_Volume01                512       976,383       975,872  83 Linux
/dev/mapper/isw_bheiihfbii_Volume02            976,894 1,953,534,975 1,952,558,082   5 Extended
/dev/mapper/isw_bheiihfbii_Volume05            976,896    10,741,759     9,764,864  82 Linux swap / Solaris
/dev/mapper/isw_bheiihfbii_Volume06         10,742,272    30,273,023    19,530,752  83 Linux
/dev/mapper/isw_bheiihfbii_Volume07         30,273,536 1,953,534,975 1,923,261,440  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bheiihfbii_Volume0p1 62d6dc7f-553e-42e6-a261-4cddf919707c   ext4       
/dev/mapper/isw_bheiihfbii_Volume0p5 2a51e751-e22d-4220-b047-7b2fc85c39f3   swap       
/dev/mapper/isw_bheiihfbii_Volume0p6 03df992a-45dd-4a22-8e12-c219f11d3a05   ext4       
/dev/mapper/isw_bheiihfbii_Volume0p7 4cac9b40-55c6-43fc-9b2a-fa5851295c2e   ext4       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bheiihfbii_Volume0
isw_bheiihfbii_Volume0p1
isw_bheiihfbii_Volume0p5
isw_bheiihfbii_Volume0p6
isw_bheiihfbii_Volume0p7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_bheiihfbii_Volume01


Unknown BootLoader on isw_bheiihfbii_Volume02


Unknown BootLoader on isw_bheiihfbii_Volume05


Unknown BootLoader on isw_bheiihfbii_Volume06


Unknown BootLoader on isw_bheiihfbii_Volume07



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_bheiihfbii_Volume01: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume01: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume02: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume02: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume05: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume05: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume06: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume06: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume07: No such file or directory
hexdump: /dev/mapper/isw_bheiihfbii_Volume07: No such file or directory

**GParted Screenshot**

---

### Post by Grimlin on 2011-10-05
Ive also tried taking the cables out of the 2nd hdd, and setting no raid, + detected 1 drive on ide in the bios. Tried to re install from live cd but couldnt see any hdd in the install partion screen.

Any ideas ?

---

