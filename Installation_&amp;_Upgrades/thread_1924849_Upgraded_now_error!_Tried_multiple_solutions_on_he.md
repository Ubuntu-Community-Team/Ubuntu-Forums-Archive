---
title: "Upgraded now error! Tried multiple solutions on here with no luck"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by braabraa on 2012-02-13
Hello all.  First time post. Which is a good thing, i have been running ubuntu for a while.  So i upgraded today and after all updates were installed I had to reboot.  After rebooting it went ot a black screen and then reset again and i received "Error:file not found. grub rescue:" I have looked and tried all the postings through out this forum with mounting back to the sda locations and tried to upgrade the grub. I am running a LiveCD from a USB drive right now.  Here is my results from "BOOT INFO SCRIPT":

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 7664 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   232,478,719   232,476,672  83 Linux
/dev/sda2         232,480,766   234,440,703     1,959,938   5 Extended
/dev/sda5         232,480,768   234,440,703     1,959,936  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9e559f9c-19df-48e3-b036-1f4b7a4fe13b   ext4       
/dev/sda5        f7f790b4-329b-46cf-b54b-ae0fa97d3999   swap       
/dev/sdb         5C4A-6247                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sdb/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f1 4b 2e 5d 36 aa c4 c9  af 4b f9 1a 2a d6 ad 45  |.K.]6....K..*..E|
00000010  15 0c 68 40 e5 9f e3 6f  b8 47 ca 5f 38 12 c0 b6  |..h@...o.G._8...|
00000020  c3 fc a4 6a ca bf 12 32  77 ec 2d 3a 93 3b 9c 1b  |...j...2w.-:.;..|
00000030  a6 1f d3 0a 60 9e 94 4f  37 60 b5 fa 52 06 23 d1  |....`..O7`..R.#.|
00000040  a6 bd 27 8c 5f 12 e8 45  81 08 32 2a cf 67 75 75  |..'._..E..2*.guu|
00000050  ec 58 11 9e c0 2f d0 ce  1d 88 b4 98 a2 95 f4 e4  |.X.../..........|
00000060  e0 b6 41 2b bc 4a 4d ea  14 c6 8e 50 a6 04 40 3a  |..A+.JM....P..@:|
00000070  2d dd a9 62 cc f9 a0 d3  b0 e6 50 a1 f2 68 3a d6  |-..b......P..h:.|
00000080  ba 10 79 af aa 10 4a 09  7a 4e cb 16 df b7 03 54  |..y...J.zN.....T|
00000090  b2 d6 23 c0 4e a5 0b 47  3a a3 10 7d 08 26 fd 91  |..#.N..G:..}.&..|
000000a0  7c f3 57 81 f1 0c e6 8a  f9 c9 70 e3 44 2a c8 aa  ||.W.......p.D*..|
000000b0  c3 6c 08 1f 0c da 1a 10  01 e6 7d 94 ac 78 45 fc  |.l........}..xE.|
000000c0  6e 86 64 07 59 e5 29 55  da 5f 06 1e 9b 05 96 24  |n.d.Y.)U._.....$|
000000d0  a7 c6 de e6 d0 41 d4 17  4e d8 1d 4e a8 06 1b ff  |.....A..N..N....|
000000e0  d8 f2 27 aa aa 44 1b 52  65 37 14 31 ad ef 76 aa  |..'..D.Re7.1..v.|
000000f0  a8 0e 30 7f 60 82 41 44  68 a0 7b 14 c3 77 86 82  |..0.`.ADh.{..w..|
00000100  01 5e 29 d2 ab d0 c5 6a  e1 7a 22 83 42 91 6e 24  |.^)....j.z".B.n$|
00000110  0c 69 83 51 84 44 69 80  99 68 1c 4c c4 74 8f 6d  |.i.Q.Di..h.L.t.m|
00000120  32 f3 f0 e8 25 32 2e 83  98 4f b9 7c 22 93 89 7a  |2...%2...O.|"..z|
00000130  1c 01 61 c4 06 2f 55 b1  27 55 8a 60 74 a4 3d a8  |..a../U.'U.`t.=.|
00000140  b3 d9 06 52 e0 11 5e 86  d0 df 60 84 14 9c cc 95  |...R..^...`.....|
00000150  20 fe 51 40 ad ec 0c c0  5b 91 4c b6 9b b0 98 1c  | .Q@....[.L.....|
00000160  cc 37 f3 7a a4 16 5e 5c  d2 51 9f 03 e1 54 41 5b  |.7.z..^\.Q...TA[|
00000170  60 88 dc 2d 40 23 96 96  7d 44 ea b8 01 3f a8 af  |`..-@#..}D...?..|
00000180  c5 35 3d c6 39 e9 35 eb  e6 ce fe 61 51 65 ef b5  |.5=.9.5....aQe..|
00000190  23 c5 88 f3 88 7b fc 19  d5 95 ec cc 6d fa 76 4a  |#....{......m.vJ|
000001a0  e5 fd 6e a0 66 31 eb 1d  53 7e 06 06 2c 74 de 8b  |..n.f1..S~..,t..|
000001b0  b3 e0 e0 fa 4d 9d 45 33  aa ad db 5c a8 88 00 fe  |....M.E3...\....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

If anyone has any incite as to how i can get this problem fixed i would really really appreciate! I am by far no expert. I have one project folder that has not been added to my dropbox folder and i cant lose it.  All you guys now how long you worked on college programming assignments lol.  Long live open source!

---

### Post by dino99 on 2012-02-13
Do a real install:
[http://ubuntuforums.org/showpost.php?p=11654218&postcount=3](http://ubuntuforums.org/showpost.php?p=11654218&postcount=3)

---

### Post by braabraa on 2012-02-13
i did have a real install up until today after it did not boot up after upgrades.  I have been installed on my disk drive for the last year and half with ubuntu and had no other problems.

---

