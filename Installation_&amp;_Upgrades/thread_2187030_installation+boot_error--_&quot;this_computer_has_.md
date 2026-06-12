---
title: "installation+boot error-- &quot;this computer has no detected opereting system&quot;"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by pambreesh on 2013-11-10
currently i have windows xp sp 3 installed on my computer , actually  earlier i installed ubuntu 13.10 successfully some days ago, that time i  was having  windows 7 with ubbuntu. but due to some reson i recently  formatted the partition of windows 7 and installed windows xp there. but  when i tried to reboot there was no grub menu and i was redirecting to  the windows xp. then i tried to reinstall ubuntu via live cd, but  i got  the above error it neither detected my windows nor the previously  installed same version of ubuntu on ext 4. when i clicked on custom  something else option there was no partition table, just an option for  sda that was my whole hard disk and if i go forword it will erase all my  hard disk important data. i can't mess with it. i also tried gparted  app but it also does not detected any partition and showing my whole  harddisk as an unallocated space. i am giving  bootinfor script result  here , so please help me please, thanks in advance .


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda3 starts at sector 102987776.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    77,818,859    77,818,797   7 NTFS / exFAT / HPFS
/dev/sda2          77,819,902   156,301,311    78,481,410   f W95 Extended (LBA)
Empty Partition.
/dev/sda3         102,987,776   144,436,337    41,448,562   7 NTFS / exFAT / HPFS

/dev/sda2 overlaps with /dev/sda3

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        68EC638AEC63517C                       ntfs       
/dev/sda3        C680FE3C80FE3293                       ntfs       local Disk
/dev/sr0                                                iso9660    Ubuntu 13.10 i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ubuntu/68EC638AEC63517C fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/ubuntu/local Disk fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  df 4e 17 08 ab d5 94 bd  63 9e 89 e3 4f 5f bd 9b  |.N......c...O_..|
00000010  48 b7 85 4b 88 db 23 5f  dc 0f 5b 8c f3 73 60 45  |H..K..#_..[..s`E|
00000020  bc db fa 82 2a c1 16 0b  a0 98 46 2f f6 d5 83 54  |....*.....F/...T|
00000030  77 9d c1 97 2c 7f 12 d3  e8 fc 20 46 d0 3e 55 bd  |w...,..... F.>U.|
00000040  a0 2e 0e e8 5c be 88 be  3c 71 0f 8a ee 91 89 96  |....\...<q......|
00000050  fe f3 cb 05 dc 99 7b ee  17 71 40 50 a4 1b 57 63  |......{..q@P..Wc|
00000060  98 0c 96 a5 1e 94 89 1c  3d dd c0 3e a5 b9 2d bf  |........=..>..-.|
00000070  64 18 be c2 db d5 27 02  64 3c 39 e2 19 74 98 9a  |d.....'.d<9..t..|
00000080  f5 14 8f ab 44 42 ef b3  8d 37 b0 ee 45 16 94 9d  |....DB...7..E...|
00000090  1f 11 cf ab 48 c5 10 42  ce 18 da 10 21 1b 8e f1  |....H..B....!...|
000000a0  b2 80 11 13 3a eb ae fe  40 31 90 61 91 a6 1f 95  |....:...@1.a....|
000000b0  a7 c3 cf a5 ea 25 64 da  59 d5 b7 64 2d 32 ff 45  |.....%d.Y..d-2.E|
000000c0  1f dd 5f dc a4 56 39 5c  87 08 f5 98 ce a4 d1 ef  |.._..V9\........|
000000d0  5c 3b dd 08 bb 81 5b 0f  33 ff 57 9e c3 d8 b1 e8  |\;....[.3.W.....|
000000e0  7b 6a c4 dd b6 4f c7 25  c0 1d 3d e4 cf 9c 3f 62  |{j...O.%..=...?b|
000000f0  d5 9e 76 2f c3 ea 0f 64  22 05 bd 50 5d b3 70 46  |..v/...d"..P].pF|
00000100  eb 14 17 fe a6 cf dd e2  51 72 c8 9b b4 21 62 4b  |........Qr...!bK|
00000110  ba 6b a3 7b 44 ae ee 26  32 4c 6b 51 df ac 97 d9  |.k.{D..&2LkQ....|
00000120  8b 06 06 ad 4f 13 ab f7  ad 3a 25 75 11 fc ca fd  |....O....:%u....|
00000130  29 0b 56 59 77 86 34 70  f2 b6 fb 50 0e 93 88 6f  |).VYw.4p...P...o|
00000140  82 13 0b 46 d0 04 ad 51  d7 0c 52 17 27 61 b3 89  |...F...Q..R.'a..|
00000150  8a 3d 4b d8 75 ae a0 49  cd 14 60 65 ec 72 46 d5  |.=K.u..I..`e.rF.|
00000160  e2 ae fd e2 a8 6e 06 9e  a0 73 17 c2 a4 97 b5 ce  |.....n...s......|
00000170  67 d0 42 fc 73 3f 71 2b  2e 99 4b 08 20 69 dc 10  |g.B.s?q+..K. i..|
00000180  27 6f 77 b8 e8 ca b2 f3  78 77 2e fb 2f 59 93 bc  |'ow.....xw../Y..|
00000190  b2 7f ba 4b 5a 16 82 cd  15 9c 31 dc 68 ed a6 9c  |...KZ.....1.h...|
000001a0  b0 de b3 b3 48 71 ae 79  a3 9f 4b a5 6f 88 fa 56  |....Hq.y..K.o..V|
000001b0  0e c4 e7 03 78 64 2a a8  57 0e d3 a8 65 d0 00 00  |....xd*.W...e...|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

  No volume groups found

---

