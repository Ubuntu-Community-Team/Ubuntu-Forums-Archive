---
title: "Gparted shows wrong partitions kubuntu 10.04"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by andapo on 2011-03-10
Hi to all.

I am trying to install kubuntu in a dell xps 16 laptop. I have already install Windows 7 in 2 partitions (C: Windows, D: Data).
Also there are 2 more partitions. A very small one that I don't know what it is and a recovery partition from dell. 
I create and an unallocated partition in order to install kubuntu. Here is my snapshot from windows 7:

[http://img130.imageshack.us/i/85081820.png/](http://img130.imageshack.us/i/85081820.png/)

When I try to install kubuntu gparted shows wrong partitions. I installed kubuntu through wubi in order to see more things. I have attached a snapshot from gparted.
[IMG]http://img7.imageshack.us/i/snapshot1su.png/[/IMG]
[IMG]http://ubuntuforums.org/home/andreas/Documents/snapshot1.png[/IMG]http://img7.imageshack.us/i/snapshot1su.png/

I also install gdisk and I execute the command sudo gdisk -l /dev/sda. Here are my results:
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Exact type match not found for type code DE00; assigning type code for
'Linux/Windows data'
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 79DB5641-E634-44D6-8E4E-AC5F8F313503
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 1-sector boundaries
Total free space is 388254380 sectors (185.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63           80324   39.2 MiB    0700  Linux/Windows data
   2           80325        30800324   14.6 GiB    4200  Windows LDM data
   3        30800325        30801919   797.5 KiB   4200  Windows LDM data
   4        30801920       236888063   98.3 GiB    4200  Windows LDM data

I know that i can use kubuntu with wubi but I cannot set the partitions for swap and home directory that are critical for me. Also the limit of 30 Gbytes is not enough for me.

Any solution?
Thanks

---

### Post by ajgreeny on 2011-03-10
From a live ubuntu CD run **system->administration->gparted** and post a screenshot of what it finds.

Also running the live CD, click on the boot-info-script link in my signature and follow the instructions.  The RESULTS.txt file will be a great help.

You probably already have the four primary partitions that are possible on the computer disk, so a re-think of partition setup may be needed.

---

### Post by andapo on 2011-03-10
Here is the result of your program
                ```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 80325. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. The info in 
                       the boot sector on the starting sector of the MFT 
                       Mirror is wrong. According to the info in the boot 
                       sector, sda1 has 30719999 sectors, but according to 
                       the info from fdisk, it has 80261 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 30801920. But according to the info from 
                       fdisk, sda2 starts at sector 80325. According to the 
                       info in the boot sector, sda2 has 206086143 sectors, 
                       but according to the info from fdisk, it has 30719999 
                       sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 236888064. But according to the info from 
                       fdisk, sda3 starts at sector 30800325. The info in 
                       boot sector on the starting sector of the MFT is 
                       wrong. According to the info in the boot sector, sda3 
                       has 240607231 sectors, but according to the info from 
                       fdisk, it has 1594 sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000  42 SFS
/dev/sda3          30,800,325    30,801,919         1,595  42 SFS
/dev/sda4          30,801,920   236,888,063   206,086,144  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3486dfa3-400c-46cb-8a53-2e4129f46847   ext4                                     
/dev/sda1        3A08558208553E57                       ntfs       RECOVERY                      
/dev/sda2        A8466EB7466E8642                       ntfs                                     
/dev/sda3        D8EACE67EACE420C                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  49 84 1f 07 00 00 00 00  |FILE0...I.......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  05 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  4a 82 90 54 e2 b5 ca 01  4a 82 90 54 e2 b5 ca 01  |J..T....J..T....|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  4a 82 90 54 e2 b5 ca 01  |........J..T....|
000000c0  4a 82 90 54 e2 b5 ca 01  4a 82 90 54 e2 b5 ca 01  |J..T....J..T....|
000000d0  4a 82 90 54 e2 b5 ca 01  00 40 00 00 00 00 00 00  |J..T.....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 0a 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 a4 00 00 00 00 00  |@...............|
00000130  00 00 a4 00 00 00 00 00  00 00 a4 00 00 00 00 00  |................|
00000140  32 40 0a 00 00 0c 00 d9  b0 00 00 00 50 00 00 00  |2@..........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  31 01 ff ff 0b 31 01 04  |........1....1..|
00000190  4c 11 00 00 00 60 2d 86  ff ff ff ff 00 00 00 00  |L....`-.........|
000001a0  00 00 01 00 00 00 00 00  31 10 00 00 0c 00 70 a8  |........1.....p.|
000001b0  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001e0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 00 00 00  ff ff ff ff 00 00 05 00  |1...............|
00000200
MFT Sector of sda3

00000000  46 49 4c 45 30 00 03 00  4e ba 52 08 00 00 00 00  |FILE0...N.R.....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  24 00 ff ff 00 00 00 00  10 00 00 00 60 00 00 00  |$...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  a3 ae 4b cd 56 de cb 01  a3 ae 4b cd 56 de cb 01  |..K.V.....K.V...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  a3 ae 4b cd 56 de cb 01  |..........K.V...|
000000c0  a3 ae 4b cd 56 de cb 01  a3 ae 4b cd 56 de cb 01  |..K.V.....K.V...|
000000d0  a3 ae 4b cd 56 de cb 01  00 40 00 00 00 00 00 00  |..K.V....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  bf 41 00 00 00 00 00 00  |.........A......|
00000120  40 00 00 00 00 00 00 00  00 00 1c 04 00 00 00 00  |@...............|
00000130  00 00 1c 04 00 00 00 00  00 00 1c 04 00 00 00 00  |................|
00000140  32 c0 41 00 00 0c 00 ff  b0 00 00 00 58 00 00 00  |2.A.........X...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  03 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 40 00 00 00 00 00 00  08 30 00 00 00 00 00 00  |.@.......0......|
00000180  08 30 00 00 00 00 00 00  31 01 ff ff 0b 11 01 ff  |.0......1.......|
00000190  31 01 ca 86 2e 41 01 79  cc fb 00 00 80 f9 ff ff  |1....A.y........|
000001a0  ff ff ff ff 00 00 00 00  31 40 00 00 0c 00 ff ff  |........1@......|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 6a df 03 80 fa 24 00  |1........j....$.|
00000200
Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

```
And here is the snapshot from gparted which is the same as before:
[http://img809.imageshack.us/i/snapshot1qf.png/](http://img809.imageshack.us/i/snapshot1qf.png/)

---

### Post by andapo on 2011-03-10
Anyone???

---

### Post by srs5694 on 2011-03-10
Your disk uses [Logical Disk Manager (LDM),](http://en.wikipedia.org/wiki/Logical_Disk_Manager) aka "dynamic disks." This is a Windows-only technology, and as long as your disk uses LDM, you'll find it difficult or impossible to install Linux on the computer. Linux can read LDM volumes, but it can't manage them, and AFAIK Ubuntu provides poor or no support for installing to or booting from LDM.

Your best bet is to back up (for safety) and then use [PartitionWizard](http://www.partitionwizard.com) or some other tool to convert your LDM configuration to a standard configuration using regular partitions. Alternatively, you could back up, wipe your current partitions, and restore everything into conventional partitions.

Also and FWIW, I'm the author of GPT fdisk (gdisk), and you should not be using it on your disk as it is now, or on your disk after you convert it. GPT fdisk is intended for use on GUID Partition Table (GPT) disks, which yours is not. It presented information because it automatically converted from your underlying partition table scheme to GPT and then showed the converted GPT partitions; but if you were to save your partition table from within gdisk, Windows would be rendered unbootable, and recovering would be very difficult. If Windows still boots, you did no damage, but you should be aware of the risks of using inappropriate partitioning tools on your hard disk. They deal with sensitive data structures, and using the wrong tool or using the right tool inappropriately *will* lead to trouble. (In fact, it probably led you to it already; chances are you had a conventional layout, but when you added a fifth partition to your disk, Windows converted to an LDM setup rather than create a logical partition, as you'd have done in most other OSes' partitioning tools.)

Finally, in the future, when posting text you cut-and-paste from a Terminal window, please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This will preserve the formatting, thus improving legibility. It will also create a scrollable box that will make it easier to scan over long output like the Boot Info Script results.

---

### Post by andapo on 2011-03-10
Thank you very much for your reply.

Actually I find the answer after hours of searching around the web. I think the answer was from you :-)

I decide to:

1. Backup Local Disk D
2. Delete Partition of Local Disk D
3. Extend the Partition of Windows C in order to install kubuntu through wubi
4. Install wubi in C drive and create additional virtual drives in order to increase disk size.

Andreas

---

### Post by srs5694 on 2011-03-10
That will work; however, you should be aware that WUBI installations are a bit limiting and are sometimes flaky -- at least, that's the impression I get from reading about them. (I've never installed this way myself.)

---

### Post by andapo on 2011-03-10
Yes it works just fine. I just increase the size of C drive in order to have the available space for wubi virtual drives.

You can very easily add an additional virtual drive:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

As I know with wubi you have only some performance issues with the virtual disk drives. What other limitations you know?

---

