---
title: "Ubuntu won't install on nvidia sata"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by cole454 on 2010-07-07
I've been trying for a couple days to install Ubuntu 10.04 on my desktop after using for a couple months on my laptop.

My desktop has an Asus M2N32-SLI mobo, with a single 100GB HDD.

I currently have Win7 installed and have resized the partitions using gparted from within the Ubuntu LiveCD.

When I start the install from the icon on the desktop it goes until it asks where to install and then it doesn't show any drives at all.

Most of the things I see pertaining to the nvidia chipset and HDDs talks about RAID. But I am not running any kind of RAID. Just a single HDD.

Please point me in the right direction. Thanks

---

### Post by Rubi1200 on 2010-07-07
> **cole454 said:**
> I've been trying for a couple days to install Ubuntu 10.04 on my desktop after using for a couple months on my laptop.

My desktop has an Asus M2N32-SLI mobo, with a single 100GB HDD.

I currently have Win7 installed and have resized the partitions using gparted from within the Ubuntu LiveCD.

When I start the install from the icon on the desktop it goes until it asks where to install and then it doesn't show any drives at all.

Most of the things I see pertaining to the nvidia chipset and HDDs talks about RAID. But I am not running any kind of RAID. Just a single HDD.

Please point me in the right direction. Thanks

Are you still able to boot into Windows normally?

When did you resize the partition and what kind of time-frame was there before you tried installing Ubuntu?

Next step:
Use the Ubuntu CD and choose the option to try in live mode not install.

Click on the link at the bottom of my post and follow the instructions there before posting the results back here.

---

### Post by ronparent on 2010-07-07
Has the drive ever been used as a raid even though the raid bios is not now engaged? Try typing 'sudo dmraid -s' in a terminal - if the output shows no raid then that is not an issue.

What happens if you pick the 3rd option to specify where you want to install?

---

### Post by cole454 on 2010-07-07
Windows boots fine.

I resized the partition from the LiveCD and then tried to install from the icon on the desktop.

Here is RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/sil_aibgebcdagdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda5 already mounted or sda5 busy

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sil_aibgebcdagdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sil_aibgebcdagdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sil_aibgebcdagdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sil_aibgebcdagdc5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda5 already mounted or sda5 busy
mount: unknown filesystem type ''

sil_aibgebcdagdc6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda5 already mounted or sda5 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   134,785,349   134,578,502   7 HPFS/NTFS
/dev/sda3         134,785,350   195,800,219    61,014,870   5 Extended
/dev/sda5         134,785,413   187,414,289    52,628,877  83 Linux
/dev/sda6         187,414,353   195,800,219     8,385,867  82 Linux swap / Solaris


Drive: sil_aibgebcdagdc ___________________ _____________________________________________________

Disk /dev/mapper/sil_aibgebcdagdc: 100.0 GB, 100029169664 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195369472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/sil_aibgebcdagdc1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/sil_aibgebcdagdc2            206,848   134,785,349   134,578,502   7 HPFS/NTFS
/dev/mapper/sil_aibgebcdagdc3        134,785,350   195,800,219    61,014,870   5 Extended
/dev/mapper/sil_aibgebcdagdc5        134,785,413   187,414,289    52,628,877  83 Linux
/dev/mapper/sil_aibgebcdagdc6        187,414,353   195,800,219     8,385,867  82 Linux swap / Solaris

/dev/mapper/sil_aibgebcdagdc3 ends after the last sector of /dev/mapper/sil_aibgebcdagdc
/dev/mapper/sil_aibgebcdagdc6 ends after the last sector of /dev/mapper/sil_aibgebcdagdc

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/sil_aibgebcdagdc1 E238B68A38B65D6B                       ntfs       System Reserved               
/dev/mapper/sil_aibgebcdagdc2 4454B83454B82B16                       ntfs                                     
/dev/mapper/sil_aibgebcdagdc: PTTYPE="dos" 
/dev/sda1        E238B68A38B65D6B                       ntfs       System Reserved               
/dev/sda2        4454B83454B82B16                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ec3b33e0-ac34-4557-a7da-74551ccf1376   ext3                                     
/dev/sda6        1a2fc6f6-d2e4-4b53-9028-5ffbbdbeea86   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/mapper/sil_aibgebcdagdc3: No such file or directory
error: /dev/mapper/sil_aibgebcdagdc5: No such file or directory
error: /dev/mapper/sil_aibgebcdagdc6: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  0d e1 a4 24 93 40 60 e0  24 29 2e 80 08 77 f6 a0  |...$.@`.$)...w..|
00000010  d0 40 05 a0 18 20 af b8  15 01 da 4b 5b 7c 31 41  |.@... .....K[|1A|
00000020  c3 2f 9e 81 84 78 72 66  e7 69 80 58 8e 64 b0 15  |./...xrf.i.X.d..|
00000030  4e bf a9 00 5c 08 00 9e  1b c0 33 0d 40 05 e0 31  |N...\.....3.@..1|
00000040  e5 00 e9 00 38 03 18 0b  86 8a ee ec 2e e3 93 41  |....8..........A|
00000050  00 15 80 14 00 6a 18 84  00 e8 b0 d2 67 ec e5 a0  |.....j......g...|
00000060  be 9f f3 ac f7 3e f0 fc  01 a0 61 0f 84 a3 7d 56  |.....>....a...}V|
00000070  4c 00 6c 50 60 0e 11 91  85 68 00 b1 11 c9 a9 e6  |L.lP`....h......|
00000080  df 40 03 00 06 44 20 07  80 3a 21 01 42 61 44 a0  |.@...D ..:!.BaD.|
00000090  c0 28 18 84 6c c0 78 ac  47 be 80 08 1f 9c 00 9c  |.(..l.x.G.......|
000000a0  b0 04 60 0f cb ee 02 82  12 79 41 85 6d b6 cd d9  |..`......yA.m...|
000000b0  ff 67 ff df 2b 21 80 e8  02 80 d5 00 91 2b 0e be  |.g..+!.......+..|
000000c0  98 4c 00 26 26 01 92 cb  4a 7a 46 86 96 d8 04 7e  |.L.&&...JzF....~|
000000d0  c0 04 08 46 3f 5b 80 9d  29 6c de fd 01 40 0f 03  |...F?[..)l...@..|
000000e0  48 61 a4 8e 91 c3 b5 8c  84 00 b8 9a 57 39 3f 98  |Ha..........W9?.|
000000f0  e7 5e 50 01 f0 02 c0 13  00 68 30 00 fc 62 06 8f  |.^P......h0..b..|
00000100  b9 00 30 00 68 00 f0 9b  b0 ce 19 ec 09 66 5a a0  |..0.h........fZ.|
00000110  a7 bf 6c 05 01 00 0e 80  35 00 5e 5a 0a 01 27 3d  |..l.....5.^Z..'=|
00000120  94 d7 28 84 00 50 1a 00  58 58 60 0c 09 a4 b0 d0  |..(..P..XX`.....|
00000130  0d 09 a9 41 2c 79 30 37  75 06 a3 9f 87 7b c7 00  |...A,y07u....{..|
00000140  c0 0a 00 e8 04 0a 0c 60  ea e0 07 60 17 60 07 a4  |.......`...`.`..|
00000150  c4 95 8b d9 3f 4c 96 b8  2c 33 fb ee 80 2d 00 7c  |....?L..,3...-.||
00000160  01 90 03 11 a0 1a 01 40  13 93 00 76 92 66 dc b0  |.......@...v.f..|
00000170  28 8e 84 f4 28 0f 9b 6d  00 74 00 d0 01 e8 01 11  |(...(..m.t......|
00000180  60 07 e1 85 24 00 e9 3f  62 18 14 30 60 13 d8 cf  |`...$..?b..0`...|
00000190  ad 60 31 40 68 01 20 06  bc 07 60 0f 00 40 9e 03  |.`1@h. ...`..@..|
000001a0  b4 16 08 5f f0 94 b3 13  71 ab 20 de 3c 01 60 03  |..._....q. .<.`.|
000001b0  90 18 00 15 80 64 4b 42  9d 0c 4d 0c e7 94 00 fe  |.....dKB..M.....|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 8d 0d 23 03 00 fe  |......?.....#...|
000001d0  ff ff 05 fe ff ff cc 0d  23 03 8a f5 7f 00 00 00  |........#.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sil_aibgebcdagdc3


Unknown BootLoader  on sil_aibgebcdagdc5


Unknown BootLoader  on sil_aibgebcdagdc6



=============================== StdErr Messages: ===============================

ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: wrong # of devices in RAID set "sil_aibgebcdagdc" [1/2] on /dev/sda
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: wrong # of devices in RAID set "sil_aibgebcdagdc" [1/2] on /dev/sda
ERROR: creating degraded mirror mapping for "sil_aibgebcdagdc"
ERROR: dos: partition address past end of RAID device
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: wrong # of devices in RAID set "sil_aibgebcdagdc" [1/2] on /dev/sda
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: wrong # of devices in RAID set "sil_aibgebcdagdc" [1/2] on /dev/sda
hexdump: /dev/mapper/sil_aibgebcdagdc3: No such file or directory
hexdump: /dev/mapper/sil_aibgebcdagdc3: No such file or directory
hexdump: /dev/mapper/sil_aibgebcdagdc5: No such file or directory
hexdump: /dev/mapper/sil_aibgebcdagdc5: No such file or directory
hexdump: /dev/mapper/sil_aibgebcdagdc6: No such file or directory
hexdump: /dev/mapper/sil_aibgebcdagdc6: No such file or directory
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: wrong # of devices in RAID set "sil_aibgebcdagdc" [1/2] on /dev/sda
ERROR: dos: partition address past end of RAID device
```

---

### Post by cole454 on 2010-07-07
> **ronparent said:**
> Has the drive ever been used as a raid even though the raid bios is not now engaged? Try typing 'sudo dmraid -s' in a terminal - if the output shows no raid then that is not an issue.

What happens if you pick the 3rd option to specify where you want to install?


Result from command

```
ubuntu@ubuntu:~$ sudo dmraid -s
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: wrong # of devices in RAID set "sil_aibgebcdagdc" [1/2] on /dev/sda
*** *Inconsistent* Set
name   : sil_aibgebcdagdc
size   : 195369472
stride : 256
type   : mirror
status : inconsistent
subsets: 0
devs   : 1
spares : 0

```


This seems all kind of weird.

---

### Post by Rubi1200 on 2010-07-07
Yes, there seem to be some odd things going on.

Also, did you run the bootscript from the LiveCD?

It is reporting 
> Device or resource busy

---

### Post by cole454 on 2010-07-07
> **Rubi1200 said:**
> Yes, there seem to be some odd things going on.

Also, did you run the bootscript from the LiveCD?

It is reporting

Yes, I did run it from the LiveCD.

This drive was part of a RAID 0 set years ago. But its been formated countless times since then out of the array.

Its like theres still some RAID info on the drive thats not getting wiped off. I dunno though, just throwing stuff out there.

---

### Post by cole454 on 2010-07-07
Well I gave up and used an old IDE drive I had and am currently installing Ubuntu.

---

### Post by confused57 on 2010-07-07
I've seen in other posts that dmraid can be removed?:
[http://ubuntuforums.org/showthread.php?t=1506552](http://ubuntuforums.org/showthread.php?t=1506552)

---

### Post by Rubi1200 on 2010-07-07
On the face of it, there is a good chance that the RAID metadata was not removed, even with formatting.

From the post linked to above by confused57:

[http://ubuntuforums.org/showpost.php?p=9447593&postcount=3](http://ubuntuforums.org/showpost.php?p=9447593&postcount=3)

I can recommend any advice darkod offers; he is one of the more experienced forum members.

---

### Post by ronparent on 2010-07-07
RAID metadata is not removed, even with formatting. Using dmraid to erase is the only way and has no repercussion on non raid drives.

---

