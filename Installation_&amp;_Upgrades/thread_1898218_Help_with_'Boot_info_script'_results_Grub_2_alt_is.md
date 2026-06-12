---
title: "Help with 'Boot info script' results? Grub 2 alt iso install failed. RAID10"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by Mentedealerta on 2011-12-20
[INDENT]First off, before anything..I would just like to say how amazing this forum is and thank you all for how much info you all have directed me to. It's awesome! With that being said, here's my problem..
  
I'm having tourble installing Grub 2 from the Ubuntu 11.10 alternate iso image. I'm currently on a 4 disk RAID setup and followed the guide [here]("http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/"). When I tried to install Grub 2, I encountered an error. I can't remember the specific problem but Grub 2 install failed. I continued the install without the bootloader where I was told I could

> 
boot manually with /vmlinuz kernel on partition /dev/mapper/os--vg-root--lv and root=/dev/mapper/os--vg-root--lv passed as a kernel argument.
When everything finished I rebooted my system and found myself caught in a bootloop. I can't figure out what to do, so I downloaded 'Boot info script' from there [website]("http://bootinfoscript.sourceforge.net"). If anyone could help me, that would be awesome. I would like to continue setting up this system but I don't understand Grub 2 or the system well enough to get the system up and booting properly.

Any recommendations?
[NOTE] SDE1 is the pendrive I'm running UbuntuLive from right now.


Here are the results to bootinfoscript


```
                   
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    108774 of the same hard drive for core.img, but core.img can not be found 
    at this location.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 7672 of /dev/sde1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       160,649       160,587  fd Linux raid autodetect
/dev/sda2             160,650       947,834       787,185  fd Linux raid autodetect
/dev/sda3             947,835   156,249,999   155,302,165  fd Linux raid autodetect


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63       160,649       160,587  fd Linux raid autodetect
/dev/sdb2             160,650       947,834       787,185  fd Linux raid autodetect
/dev/sdb3             947,835   156,249,999   155,302,165  fd Linux raid autodetect


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63       160,649       160,587  fd Linux raid autodetect
/dev/sdc2             160,650       947,834       787,185  fd Linux raid autodetect
/dev/sdc3             947,835   156,249,999   155,302,165  fd Linux raid autodetect


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63       160,649       160,587  fd Linux raid autodetect
/dev/sdd2             160,650       947,834       787,185  fd Linux raid autodetect
/dev/sdd3             947,835   156,249,999   155,302,165  fd Linux raid autodetect


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sde _____________________________________________________________________

Disk /dev/sde: 2003 MB, 2003795968 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63     3,913,663     3,913,601   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        ff0bff2b-579e-02bd-713e-e83cf0c92538   linux_raid_member ubuntu:0
/dev/sda2        b7df9bba-8905-76b3-92d9-9319516f4f05   linux_raid_member ubuntu:1
/dev/sda3        0b7a01d0-60fc-9480-fc73-a11b1705e658   linux_raid_member ubuntu:2
/dev/sdb1        ff0bff2b-579e-02bd-713e-e83cf0c92538   linux_raid_member ubuntu:0
/dev/sdb2        b7df9bba-8905-76b3-92d9-9319516f4f05   linux_raid_member ubuntu:1
/dev/sdb3        0b7a01d0-60fc-9480-fc73-a11b1705e658   linux_raid_member ubuntu:2
/dev/sdc1        ff0bff2b-579e-02bd-713e-e83cf0c92538   linux_raid_member ubuntu:0
/dev/sdc2        b7df9bba-8905-76b3-92d9-9319516f4f05   linux_raid_member ubuntu:1
/dev/sdc3        0b7a01d0-60fc-9480-fc73-a11b1705e658   linux_raid_member ubuntu:2
/dev/sde1        3C40-2138                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sde1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  5d 89 ea 12 21 86 12 55  f4 86 fd b0 81 d1 92 45  |]...!..U.......E|
00000010  64 8b 10 3e c8 a0 b0 66  55 f7 81 cc 13 5e b7 ed  |d..>...fU....^..|
00000020  8e 38 91 4c 48 ff 5b 86  b5 23 71 c3 45 c4 89 44  |.8.LH.[..#q.E..D|
00000030  8e 1f 5a 5e 0d d9 4b ce  e1 86 af ec 82 c7 49 44  |..Z^..K.......ID|
00000040  e2 9b eb 6e 5a 4b 1c ee  06 04 86 ee c1 82 86 3c  |...nZK.........<|
00000050  13 e4 95 f6 b6 f7 c8 4d  94 32 9b 7c 1c 6a 2b b9  |.......M.2.|.j+.|
00000060  00 69 cb 03 b7 09 ff e3  15 39 92 db f0 8b b0 5b  |.i.......9.....[|
00000070  65 ea 5d c8 37 43 6d 02  00 00 8d b4 ea ed 0b fa  |e.].7Cm.........|
00000080  b0 86 04 33 7e 36 28 cf  ec 3f ec 13 f4 e8 05 d1  |...3~6(..?......|
00000090  51 f0 56 6d da 5a 9c a6  9e 0c d1 b8 0b 34 9e 1f  |Q.Vm.Z.......4..|
000000a0  6a 95 5b f7 d6 8b 62 65  84 d7 29 61 56 56 b3 87  |j.[...be..)aVV..|
000000b0  ca 3b 95 8e 22 8e a1 e4  82 fa 2c ff f3 25 49 f4  |.;..".....,..%I.|
000000c0  03 17 b7 77 b7 f7 f4 0b  c2 7b df c3 bf 6e 13 4a  |...w.....{...n.J|
000000d0  14 9c c0 1e 58 c1 8f 91  fe c9 a9 c8 5c 42 0b 66  |....X.......\B.f|
000000e0  86 fa 57 31 60 67 0f e8  b7 f7 f4 e8 2b 45 04 41  |..W1`g......+E.A|
000000f0  3d 7d af 22 03 03 83 d8  18 c4 24 c1 e0 10 89 f8  |=}."......$.....|
00000100  c9 a7 d2 02 b5 d4 68 72  72 d9 fa 90 89 48 da 3f  |......hrr....H.?|
00000110  5b 64 07 78 f1 8b 72 04  18 da 40 c9 ec 03 83 e6  |[d.x..r...@.....|
00000120  94 c9 aa 2b 09 d6 c1 2b  1d fc c6 0f b8 65 02 7a  |...+...+.....e.z|
00000130  5e 7a f0 c1 21 6e 42 6a  15 82 32 37 0b 8a 10 0f  |^z..!nBj..27....|
00000140  5d c1 28 5c 69 ad 33 68  71 a1 c3 bf 54 0d 0f 0d  |].(\i.3hq...T...|
00000150  f4 1f 87 52 95 2f 6a 2b  78 0b 0c 93 0e c7 44 24  |...R./j+x.....D$|
00000160  04 0f 8e 08 0f f5 1f b1  b0 95 78 45 45 18 cb 68  |..........xEE..h|
00000170  c8 53 c3 8d b6 00 93 8e  08 8d bc 27 00 cb 0b 3d  |.S.........'...=|
00000180  ff 86 32 25 e9 6a ac 65  5d 99 09 c5 e3 1f 9b f6  |..2%.j.e].......|
00000190  fd ab e5 90 80 90 2f d8  e8 1b b4 26 1e 01 5b 00  |....../....&..[.|
000001a0  55 89 f2 16 5b 05 0c 8b  10 0b 5b 0f 8f 02 c0 c3  |U...[.....[.....|
000001b0  5e 39 df 18 6f 30 ec 63  f4 ad fa 8d 75 b7 33 1b  |^9..o0.c....u.3.|
000001c0  07 fa d5 86 f5 bc 91 ee  74 c1 ff ea c7 cf fb f0  |........t.......|
000001d0  f9 8b 37 dc 45 20 f4 b0  59 74 2d 6a 4b ac 50 9d  |..7.E ..Yt-jK.P.|
000001e0  88 b2 1c a7 c7 0f 60 a6  22 b7 8f c2 17 65 09 cc  |......`."....e..|
000001f0  82 ce f1 03 05 0d d8 82  c8 34 07 85 cb 93 b9 6f  |.........4.....o|
00000200

Unknown BootLoader on sda3

00000000  ce 73 5a 91 58 26 cf 3b  75 b2 c6 75 6d 16 5b c8  |.sZ.X&.;u..um.[.|
00000010  fa 4c 32 2b 48 ce 50 bc  5b 6f 51 ec 70 c3 3f 11  |.L2+H.P.[oQ.p.?.|
00000020  36 6c 79 0d 3a 4c db 21  07 b7 ff 49 72 6a fa b6  |6ly.:L.!...Irj..|
00000030  b0 3b c0 53 61 5c 96 d3  7b de 5c 97 29 82 fe 5e  |.;.Sa\..{.\.)..^|
00000040  87 22 d5 7a 79 9c 06 dc  77 11 17 8c 95 11 2e 18  |.".zy...w.......|
00000050  a1 53 83 ef 7c 04 80 db  b5 00 8a e4 57 ff f9 0d  |.S..|.......W...|
00000060  cd 08 b6 da 96 a7 6b 54  82 23 79 0b 3b 9a c7 87  |......kT.#y.;...|
00000070  a4 e9 e6 db 34 2f bf e3  14 2d 31 bb 04 48 40 bd  |....4/...-1..H@.|
00000080  1a b6 f4 49 57 6b 74 d9  fd 0f d3 35 47 cf f0 da  |...IWkt....5G...|
00000090  4b 0e 2c 07 ee b2 47 f4  f6 36 a2 28 fa a8 48 7f  |K.,...G..6.(..H.|
000000a0  f5 c9 11 9b 18 16 ab a2  30 49 50 ff 8b 99 19 f5  |........0IP.....|
000000b0  1d 24 9a 98 00 ce 2e 06  63 7b f1 15 16 70 68 e9  |.$......c{...ph.|
000000c0  10 92 68 81 9d 31 aa ac  0a d9 95 46 c9 8d ad c8  |..h..1.....F....|
000000d0  ec 1b f2 55 4f cc 05 e4  ae e7 ba 14 31 c4 19 81  |...UO.......1...|
000000e0  70 a5 74 08 8d 80 4b 23  e1 41 28 fd c3 9d 6e d9  |p.t...K#.A(...n.|
000000f0  37 d5 70 5f d7 50 9f e0  86 7a 3c 25 20 14 f9 ed  |7.p_.P...z<% ...|
00000100  70 b5 a9 4b 49 71 85 70  03 35 79 fd d0 d4 e9 00  |p..KIq.p.5y.....|
00000110  4e 7e 23 41 ec cf 9d 77  63 49 48 7b 75 9b 49 8b  |N~#A...wcIH{u.I.|
00000120  29 9c 01 b5 64 71 9f ed  68 71 8a 8e 0b 92 7a df  |)...dq..hq....z.|
00000130  c9 df e8 72 ae 9f 98 eb  ec b1 5a 21 ca 49 0d 89  |...r......Z!.I..|
00000140  96 92 a2 49 f8 45 65 8b  e1 39 98 62 1e 72 51 0f  |...I.Ee..9.b.rQ.|
00000150  c5 ba 9d bf 2e 9e 72 4d  31 2e 49 66 72 b2 20 8c  |......rM1.Ifr. .|
00000160  4b 30 7d 47 d9 c2 48 68  e9 ac 81 23 fe f1 3d 08  |K0}G..Hh...#..=.|
00000170  9a 95 11 6e 4a 11 6e e7  c6 60 08 cf ba 66 cf 04  |...nJ.n..`...f..|
00000180  8a 31 c6 06 77 30 a5 92  cf 7f 2a fe e6 19 79 46  |.1..w0....*...yF|
00000190  cd c6 f5 1f 01 ff b2 ac  53 ad f2 d3 2b 71 30 d7  |........S...+q0.|
000001a0  a3 53 8d 40 13 a9 d0 2d  70 2c 06 fd 73 2a 01 f3  |.S.@...-p,..s*..|
000001b0  b0 93 19 32 30 ba f4 40  fa ef 4a cd e0 84 0b 84  |...20..@..J.....|
000001c0  f6 c6 2d 4c 2f aa 5f 39  8f f3 27 02 ca 50 c0 79  |..-L/._9..'..P.y|
000001d0  38 bd a8 0d 72 86 e0 77  26 c5 8b 8e 84 cb 2d 4b  |8...r..w&.....-K|
000001e0  65 4b 92 10 aa a9 d9 93  11 14 34 ef cb d8 e4 94  |eK........4.....|
000001f0  73 fa e0 0a ab b5 c9 ee  cf 15 c4 4f 32 a9 59 68  |s..........O2.Yh|
00000200

Unknown BootLoader on sdb2

00000000  5d 89 ea 12 21 86 12 55  f4 86 fd b0 81 d1 92 45  |]...!..U.......E|
00000010  64 8b 10 3e c8 a0 b0 66  55 f7 81 cc 13 5e b7 ed  |d..>...fU....^..|
00000020  8e 38 91 4c 48 ff 5b 86  b5 23 71 c3 45 c4 89 44  |.8.LH.[..#q.E..D|
00000030  8e 1f 5a 5e 0d d9 4b ce  e1 86 af ec 82 c7 49 44  |..Z^..K.......ID|
00000040  e2 9b eb 6e 5a 4b 1c ee  06 04 86 ee c1 82 86 3c  |...nZK.........<|
00000050  13 e4 95 f6 b6 f7 c8 4d  94 32 9b 7c 1c 6a 2b b9  |.......M.2.|.j+.|
00000060  00 69 cb 03 b7 09 ff e3  15 39 92 db f0 8b b0 5b  |.i.......9.....[|
00000070  65 ea 5d c8 37 43 6d 02  00 00 8d b4 ea ed 0b fa  |e.].7Cm.........|
00000080  b0 86 04 33 7e 36 28 cf  ec 3f ec 13 f4 e8 05 d1  |...3~6(..?......|
00000090  51 f0 56 6d da 5a 9c a6  9e 0c d1 b8 0b 34 9e 1f  |Q.Vm.Z.......4..|
000000a0  6a 95 5b f7 d6 8b 62 65  84 d7 29 61 56 56 b3 87  |j.[...be..)aVV..|
000000b0  ca 3b 95 8e 22 8e a1 e4  82 fa 2c ff f3 25 49 f4  |.;..".....,..%I.|
000000c0  03 17 b7 77 b7 f7 f4 0b  c2 7b df c3 bf 6e 13 4a  |...w.....{...n.J|
000000d0  14 9c c0 1e 58 c1 8f 91  fe c9 a9 c8 5c 42 0b 66  |....X.......\B.f|
000000e0  86 fa 57 31 60 67 0f e8  b7 f7 f4 e8 2b 45 04 41  |..W1`g......+E.A|
000000f0  3d 7d af 22 03 03 83 d8  18 c4 24 c1 e0 10 89 f8  |=}."......$.....|
00000100  c9 a7 d2 02 b5 d4 68 72  72 d9 fa 90 89 48 da 3f  |......hrr....H.?|
00000110  5b 64 07 78 f1 8b 72 04  18 da 40 c9 ec 03 83 e6  |[d.x..r...@.....|
00000120  94 c9 aa 2b 09 d6 c1 2b  1d fc c6 0f b8 65 02 7a  |...+...+.....e.z|
00000130  5e 7a f0 c1 21 6e 42 6a  15 82 32 37 0b 8a 10 0f  |^z..!nBj..27....|
00000140  5d c1 28 5c 69 ad 33 68  71 a1 c3 bf 54 0d 0f 0d  |].(\i.3hq...T...|
00000150  f4 1f 87 52 95 2f 6a 2b  78 0b 0c 93 0e c7 44 24  |...R./j+x.....D$|
00000160  04 0f 8e 08 0f f5 1f b1  b0 95 78 45 45 18 cb 68  |..........xEE..h|
00000170  c8 53 c3 8d b6 00 93 8e  08 8d bc 27 00 cb 0b 3d  |.S.........'...=|
00000180  ff 86 32 25 e9 6a ac 65  5d 99 09 c5 e3 1f 9b f6  |..2%.j.e].......|
00000190  fd ab e5 90 80 90 2f d8  e8 1b b4 26 1e 01 5b 00  |....../....&..[.|
000001a0  55 89 f2 16 5b 05 0c 8b  10 0b 5b 0f 8f 02 c0 c3  |U...[.....[.....|
000001b0  5e 39 df 18 6f 30 ec 63  f4 ad fa 8d 75 b7 33 1b  |^9..o0.c....u.3.|
000001c0  07 fa d5 86 f5 bc 91 ee  74 c1 ff ea c7 cf fb f0  |........t.......|
000001d0  f9 8b 37 dc 45 20 f4 b0  59 74 2d 6a 4b ac 50 9d  |..7.E ..Yt-jK.P.|
000001e0  88 b2 1c a7 c7 0f 60 a6  22 b7 8f c2 17 65 09 cc  |......`."....e..|
000001f0  82 ce f1 03 05 0d d8 82  c8 34 07 85 cb 93 b9 6f  |.........4.....o|
00000200

Unknown BootLoader on sdb3

00000000  ce 73 5a 91 58 26 cf 3b  75 b2 c6 75 6d 16 5b c8  |.sZ.X&.;u..um.[.|
00000010  fa 4c 32 2b 48 ce 50 bc  5b 6f 51 ec 70 c3 3f 11  |.L2+H.P.[oQ.p.?.|
00000020  36 6c 79 0d 3a 4c db 21  07 b7 ff 49 72 6a fa b6  |6ly.:L.!...Irj..|
00000030  b0 3b c0 53 61 5c 96 d3  7b de 5c 97 29 82 fe 5e  |.;.Sa\..{.\.)..^|
00000040  87 22 d5 7a 79 9c 06 dc  77 11 17 8c 95 11 2e 18  |.".zy...w.......|
00000050  a1 53 83 ef 7c 04 80 db  b5 00 8a e4 57 ff f9 0d  |.S..|.......W...|
00000060  cd 08 b6 da 96 a7 6b 54  82 23 79 0b 3b 9a c7 87  |......kT.#y.;...|
00000070  a4 e9 e6 db 34 2f bf e3  14 2d 31 bb 04 48 40 bd  |....4/...-1..H@.|
00000080  1a b6 f4 49 57 6b 74 d9  fd 0f d3 35 47 cf f0 da  |...IWkt....5G...|
00000090  4b 0e 2c 07 ee b2 47 f4  f6 36 a2 28 fa a8 48 7f  |K.,...G..6.(..H.|
000000a0  f5 c9 11 9b 18 16 ab a2  30 49 50 ff 8b 99 19 f5  |........0IP.....|
000000b0  1d 24 9a 98 00 ce 2e 06  63 7b f1 15 16 70 68 e9  |.$......c{...ph.|
000000c0  10 92 68 81 9d 31 aa ac  0a d9 95 46 c9 8d ad c8  |..h..1.....F....|
000000d0  ec 1b f2 55 4f cc 05 e4  ae e7 ba 14 31 c4 19 81  |...UO.......1...|
000000e0  70 a5 74 08 8d 80 4b 23  e1 41 28 fd c3 9d 6e d9  |p.t...K#.A(...n.|
000000f0  37 d5 70 5f d7 50 9f e0  86 7a 3c 25 20 14 f9 ed  |7.p_.P...z<% ...|
00000100  70 b5 a9 4b 49 71 85 70  03 35 79 fd d0 d4 e9 00  |p..KIq.p.5y.....|
00000110  4e 7e 23 41 ec cf 9d 77  63 49 48 7b 75 9b 49 8b  |N~#A...wcIH{u.I.|
00000120  29 9c 01 b5 64 71 9f ed  68 71 8a 8e 0b 92 7a df  |)...dq..hq....z.|
00000130  c9 df e8 72 ae 9f 98 eb  ec b1 5a 21 ca 49 0d 89  |...r......Z!.I..|
00000140  96 92 a2 49 f8 45 65 8b  e1 39 98 62 1e 72 51 0f  |...I.Ee..9.b.rQ.|
00000150  c5 ba 9d bf 2e 9e 72 4d  31 2e 49 66 72 b2 20 8c  |......rM1.Ifr. .|
00000160  4b 30 7d 47 d9 c2 48 68  e9 ac 81 23 fe f1 3d 08  |K0}G..Hh...#..=.|
00000170  9a 95 11 6e 4a 11 6e e7  c6 60 08 cf ba 66 cf 04  |...nJ.n..`...f..|
00000180  8a 31 c6 06 77 30 a5 92  cf 7f 2a fe e6 19 79 46  |.1..w0....*...yF|
00000190  cd c6 f5 1f 01 ff b2 ac  53 ad f2 d3 2b 71 30 d7  |........S...+q0.|
000001a0  a3 53 8d 40 13 a9 d0 2d  70 2c 06 fd 73 2a 01 f3  |.S.@...-p,..s*..|
000001b0  b0 93 19 32 30 ba f4 40  fa ef 4a cd e0 84 0b 84  |...20..@..J.....|
000001c0  f6 c6 2d 4c 2f aa 5f 39  8f f3 27 02 ca 50 c0 79  |..-L/._9..'..P.y|
000001d0  38 bd a8 0d 72 86 e0 77  26 c5 8b 8e 84 cb 2d 4b  |8...r..w&.....-K|
000001e0  65 4b 92 10 aa a9 d9 93  11 14 34 ef cb d8 e4 94  |eK........4.....|
000001f0  73 fa e0 0a ab b5 c9 ee  cf 15 c4 4f 32 a9 59 68  |s..........O2.Yh|
00000200

Unknown BootLoader on sdc2

00000000  5d 89 ea 12 21 86 12 55  f4 86 fd b0 81 d1 92 45  |]...!..U.......E|
00000010  64 8b 10 3e c8 a0 b0 66  55 f7 81 cc 13 5e b7 ed  |d..>...fU....^..|
00000020  8e 38 91 4c 48 ff 5b 86  b5 23 71 c3 45 c4 89 44  |.8.LH.[..#q.E..D|
00000030  8e 1f 5a 5e 0d d9 4b ce  e1 86 af ec 82 c7 49 44  |..Z^..K.......ID|
00000040  e2 9b eb 6e 5a 4b 1c ee  06 04 86 ee c1 82 86 3c  |...nZK.........<|
00000050  13 e4 95 f6 b6 f7 c8 4d  94 32 9b 7c 1c 6a 2b b9  |.......M.2.|.j+.|
00000060  00 69 cb 03 b7 09 ff e3  15 39 92 db f0 8b b0 5b  |.i.......9.....[|
00000070  65 ea 5d c8 37 43 6d 02  00 00 8d b4 ea ed 0b fa  |e.].7Cm.........|
00000080  b0 86 04 33 7e 36 28 cf  ec 3f ec 13 f4 e8 05 d1  |...3~6(..?......|
00000090  51 f0 56 6d da 5a 9c a6  9e 0c d1 b8 0b 34 9e 1f  |Q.Vm.Z.......4..|
000000a0  6a 95 5b f7 d6 8b 62 65  84 d7 29 61 56 56 b3 87  |j.[...be..)aVV..|
000000b0  ca 3b 95 8e 22 8e a1 e4  82 fa 2c ff f3 25 49 f4  |.;..".....,..%I.|
000000c0  03 17 b7 77 b7 f7 f4 0b  c2 7b df c3 bf 6e 13 4a  |...w.....{...n.J|
000000d0  14 9c c0 1e 58 c1 8f 91  fe c9 a9 c8 5c 42 0b 66  |....X.......\B.f|
000000e0  86 fa 57 31 60 67 0f e8  b7 f7 f4 e8 2b 45 04 41  |..W1`g......+E.A|
000000f0  3d 7d af 22 03 03 83 d8  18 c4 24 c1 e0 10 89 f8  |=}."......$.....|
00000100  c9 a7 d2 02 b5 d4 68 72  72 d9 fa 90 89 48 da 3f  |......hrr....H.?|
00000110  5b 64 07 78 f1 8b 72 04  18 da 40 c9 ec 03 83 e6  |[d.x..r...@.....|
00000120  94 c9 aa 2b 09 d6 c1 2b  1d fc c6 0f b8 65 02 7a  |...+...+.....e.z|
00000130  5e 7a f0 c1 21 6e 42 6a  15 82 32 37 0b 8a 10 0f  |^z..!nBj..27....|
00000140  5d c1 28 5c 69 ad 33 68  71 a1 c3 bf 54 0d 0f 0d  |].(\i.3hq...T...|
00000150  f4 1f 87 52 95 2f 6a 2b  78 0b 0c 93 0e c7 44 24  |...R./j+x.....D$|
00000160  04 0f 8e 08 0f f5 1f b1  b0 95 78 45 45 18 cb 68  |..........xEE..h|
00000170  c8 53 c3 8d b6 00 93 8e  08 8d bc 27 00 cb 0b 3d  |.S.........'...=|
00000180  ff 86 32 25 e9 6a ac 65  5d 99 09 c5 e3 1f 9b f6  |..2%.j.e].......|
00000190  fd ab e5 90 80 90 2f d8  e8 1b b4 26 1e 01 5b 00  |....../....&..[.|
000001a0  55 89 f2 16 5b 05 0c 8b  10 0b 5b 0f 8f 02 c0 c3  |U...[.....[.....|
000001b0  5e 39 df 18 6f 30 ec 63  f4 ad fa 8d 75 b7 33 1b  |^9..o0.c....u.3.|
000001c0  07 fa d5 86 f5 bc 91 ee  74 c1 ff ea c7 cf fb f0  |........t.......|
000001d0  f9 8b 37 dc 45 20 f4 b0  59 74 2d 6a 4b ac 50 9d  |..7.E ..Yt-jK.P.|
000001e0  88 b2 1c a7 c7 0f 60 a6  22 b7 8f c2 17 65 09 cc  |......`."....e..|
000001f0  82 ce f1 03 05 0d d8 82  c8 34 07 85 cb 93 b9 6f  |.........4.....o|
00000200

Unknown BootLoader on sdc3

00000000  ce 73 5a 91 58 26 cf 3b  75 b2 c6 75 6d 16 5b c8  |.sZ.X&.;u..um.[.|
00000010  fa 4c 32 2b 48 ce 50 bc  5b 6f 51 ec 70 c3 3f 11  |.L2+H.P.[oQ.p.?.|
00000020  36 6c 79 0d 3a 4c db 21  07 b7 ff 49 72 6a fa b6  |6ly.:L.!...Irj..|
00000030  b0 3b c0 53 61 5c 96 d3  7b de 5c 97 29 82 fe 5e  |.;.Sa\..{.\.)..^|
00000040  87 22 d5 7a 79 9c 06 dc  77 11 17 8c 95 11 2e 18  |.".zy...w.......|
00000050  a1 53 83 ef 7c 04 80 db  b5 00 8a e4 57 ff f9 0d  |.S..|.......W...|
00000060  cd 08 b6 da 96 a7 6b 54  82 23 79 0b 3b 9a c7 87  |......kT.#y.;...|
00000070  a4 e9 e6 db 34 2f bf e3  14 2d 31 bb 04 48 40 bd  |....4/...-1..H@.|
00000080  1a b6 f4 49 57 6b 74 d9  fd 0f d3 35 47 cf f0 da  |...IWkt....5G...|
00000090  4b 0e 2c 07 ee b2 47 f4  f6 36 a2 28 fa a8 48 7f  |K.,...G..6.(..H.|
000000a0  f5 c9 11 9b 18 16 ab a2  30 49 50 ff 8b 99 19 f5  |........0IP.....|
000000b0  1d 24 9a 98 00 ce 2e 06  63 7b f1 15 16 70 68 e9  |.$......c{...ph.|
000000c0  10 92 68 81 9d 31 aa ac  0a d9 95 46 c9 8d ad c8  |..h..1.....F....|
000000d0  ec 1b f2 55 4f cc 05 e4  ae e7 ba 14 31 c4 19 81  |...UO.......1...|
000000e0  70 a5 74 08 8d 80 4b 23  e1 41 28 fd c3 9d 6e d9  |p.t...K#.A(...n.|
000000f0  37 d5 70 5f d7 50 9f e0  86 7a 3c 25 20 14 f9 ed  |7.p_.P...z<% ...|
00000100  70 b5 a9 4b 49 71 85 70  03 35 79 fd d0 d4 e9 00  |p..KIq.p.5y.....|
00000110  4e 7e 23 41 ec cf 9d 77  63 49 48 7b 75 9b 49 8b  |N~#A...wcIH{u.I.|
00000120  29 9c 01 b5 64 71 9f ed  68 71 8a 8e 0b 92 7a df  |)...dq..hq....z.|
00000130  c9 df e8 72 ae 9f 98 eb  ec b1 5a 21 ca 49 0d 89  |...r......Z!.I..|
00000140  96 92 a2 49 f8 45 65 8b  e1 39 98 62 1e 72 51 0f  |...I.Ee..9.b.rQ.|
00000150  c5 ba 9d bf 2e 9e 72 4d  31 2e 49 66 72 b2 20 8c  |......rM1.Ifr. .|
00000160  4b 30 7d 47 d9 c2 48 68  e9 ac 81 23 fe f1 3d 08  |K0}G..Hh...#..=.|
00000170  9a 95 11 6e 4a 11 6e e7  c6 60 08 cf ba 66 cf 04  |...nJ.n..`...f..|
00000180  8a 31 c6 06 77 30 a5 92  cf 7f 2a fe e6 19 79 46  |.1..w0....*...yF|
00000190  cd c6 f5 1f 01 ff b2 ac  53 ad f2 d3 2b 71 30 d7  |........S...+q0.|
000001a0  a3 53 8d 40 13 a9 d0 2d  70 2c 06 fd 73 2a 01 f3  |.S.@...-p,..s*..|
000001b0  b0 93 19 32 30 ba f4 40  fa ef 4a cd e0 84 0b 84  |...20..@..J.....|
000001c0  f6 c6 2d 4c 2f aa 5f 39  8f f3 27 02 ca 50 c0 79  |..-L/._9..'..P.y|
000001d0  38 bd a8 0d 72 86 e0 77  26 c5 8b 8e 84 cb 2d 4b  |8...r..w&.....-K|
000001e0  65 4b 92 10 aa a9 d9 93  11 14 34 ef cb d8 e4 94  |eK........4.....|
000001f0  73 fa e0 0a ab b5 c9 ee  cf 15 c4 4f 32 a9 59 68  |s..........O2.Yh|
00000200

Unknown BootLoader on sdd2

00000000  5d 89 ea 12 21 86 12 55  f4 86 fd b0 81 d1 92 45  |]...!..U.......E|
00000010  64 8b 10 3e c8 a0 b0 66  55 f7 81 cc 13 5e b7 ed  |d..>...fU....^..|
00000020  8e 38 91 4c 48 ff 5b 86  b5 23 71 c3 45 c4 89 44  |.8.LH.[..#q.E..D|
00000030  8e 1f 5a 5e 0d d9 4b ce  e1 86 af ec 82 c7 49 44  |..Z^..K.......ID|
00000040  e2 9b eb 6e 5a 4b 1c ee  06 04 86 ee c1 82 86 3c  |...nZK.........<|
00000050  13 e4 95 f6 b6 f7 c8 4d  94 32 9b 7c 1c 6a 2b b9  |.......M.2.|.j+.|
00000060  00 69 cb 03 b7 09 ff e3  15 39 92 db f0 8b b0 5b  |.i.......9.....[|
00000070  65 ea 5d c8 37 43 6d 02  00 00 8d b4 ea ed 0b fa  |e.].7Cm.........|
00000080  b0 86 04 33 7e 36 28 cf  ec 3f ec 13 f4 e8 05 d1  |...3~6(..?......|
00000090  51 f0 56 6d da 5a 9c a6  9e 0c d1 b8 0b 34 9e 1f  |Q.Vm.Z.......4..|
000000a0  6a 95 5b f7 d6 8b 62 65  84 d7 29 61 56 56 b3 87  |j.[...be..)aVV..|
000000b0  ca 3b 95 8e 22 8e a1 e4  82 fa 2c ff f3 25 49 f4  |.;..".....,..%I.|
000000c0  03 17 b7 77 b7 f7 f4 0b  c2 7b df c3 bf 6e 13 4a  |...w.....{...n.J|
000000d0  14 9c c0 1e 58 c1 8f 91  fe c9 a9 c8 5c 42 0b 66  |....X.......\B.f|
000000e0  86 fa 57 31 60 67 0f e8  b7 f7 f4 e8 2b 45 04 41  |..W1`g......+E.A|
000000f0  3d 7d af 22 03 03 83 d8  18 c4 24 c1 e0 10 89 f8  |=}."......$.....|
00000100  c9 a7 d2 02 b5 d4 68 72  72 d9 fa 90 89 48 da 3f  |......hrr....H.?|
00000110  5b 64 07 78 f1 8b 72 04  18 da 40 c9 ec 03 83 e6  |[d.x..r...@.....|
00000120  94 c9 aa 2b 09 d6 c1 2b  1d fc c6 0f b8 65 02 7a  |...+...+.....e.z|
00000130  5e 7a f0 c1 21 6e 42 6a  15 82 32 37 0b 8a 10 0f  |^z..!nBj..27....|
00000140  5d c1 28 5c 69 ad 33 68  71 a1 c3 bf 54 0d 0f 0d  |].(\i.3hq...T...|
00000150  f4 1f 87 52 95 2f 6a 2b  78 0b 0c 93 0e c7 44 24  |...R./j+x.....D$|
00000160  04 0f 8e 08 0f f5 1f b1  b0 95 78 45 45 18 cb 68  |..........xEE..h|
00000170  c8 53 c3 8d b6 00 93 8e  08 8d bc 27 00 cb 0b 3d  |.S.........'...=|
00000180  ff 86 32 25 e9 6a ac 65  5d 99 09 c5 e3 1f 9b f6  |..2%.j.e].......|
00000190  fd ab e5 90 80 90 2f d8  e8 1b b4 26 1e 01 5b 00  |....../....&..[.|
000001a0  55 89 f2 16 5b 05 0c 8b  10 0b 5b 0f 8f 02 c0 c3  |U...[.....[.....|
000001b0  5e 39 df 18 6f 30 ec 63  f4 ad fa 8d 75 b7 33 1b  |^9..o0.c....u.3.|
000001c0  07 fa d5 86 f5 bc 91 ee  74 c1 ff ea c7 cf fb f0  |........t.......|
000001d0  f9 8b 37 dc 45 20 f4 b0  59 74 2d 6a 4b ac 50 9d  |..7.E ..Yt-jK.P.|
000001e0  88 b2 1c a7 c7 0f 60 a6  22 b7 8f c2 17 65 09 cc  |......`."....e..|
000001f0  82 ce f1 03 05 0d d8 82  c8 34 07 85 cb 93 b9 6f  |.........4.....o|
00000200

Unknown BootLoader on sdd3

00000000  ce 73 5a 91 58 26 cf 3b  75 b2 c6 75 6d 16 5b c8  |.sZ.X&.;u..um.[.|
00000010  fa 4c 32 2b 48 ce 50 bc  5b 6f 51 ec 70 c3 3f 11  |.L2+H.P.[oQ.p.?.|
00000020  36 6c 79 0d 3a 4c db 21  07 b7 ff 49 72 6a fa b6  |6ly.:L.!...Irj..|
00000030  b0 3b c0 53 61 5c 96 d3  7b de 5c 97 29 82 fe 5e  |.;.Sa\..{.\.)..^|
00000040  87 22 d5 7a 79 9c 06 dc  77 11 17 8c 95 11 2e 18  |.".zy...w.......|
00000050  a1 53 83 ef 7c 04 80 db  b5 00 8a e4 57 ff f9 0d  |.S..|.......W...|
00000060  cd 08 b6 da 96 a7 6b 54  82 23 79 0b 3b 9a c7 87  |......kT.#y.;...|
00000070  a4 e9 e6 db 34 2f bf e3  14 2d 31 bb 04 48 40 bd  |....4/...-1..H@.|
00000080  1a b6 f4 49 57 6b 74 d9  fd 0f d3 35 47 cf f0 da  |...IWkt....5G...|
00000090  4b 0e 2c 07 ee b2 47 f4  f6 36 a2 28 fa a8 48 7f  |K.,...G..6.(..H.|
000000a0  f5 c9 11 9b 18 16 ab a2  30 49 50 ff 8b 99 19 f5  |........0IP.....|
000000b0  1d 24 9a 98 00 ce 2e 06  63 7b f1 15 16 70 68 e9  |.$......c{...ph.|
000000c0  10 92 68 81 9d 31 aa ac  0a d9 95 46 c9 8d ad c8  |..h..1.....F....|
000000d0  ec 1b f2 55 4f cc 05 e4  ae e7 ba 14 31 c4 19 81  |...UO.......1...|
000000e0  70 a5 74 08 8d 80 4b 23  e1 41 28 fd c3 9d 6e d9  |p.t...K#.A(...n.|
000000f0  37 d5 70 5f d7 50 9f e0  86 7a 3c 25 20 14 f9 ed  |7.p_.P...z<% ...|
00000100  70 b5 a9 4b 49 71 85 70  03 35 79 fd d0 d4 e9 00  |p..KIq.p.5y.....|
00000110  4e 7e 23 41 ec cf 9d 77  63 49 48 7b 75 9b 49 8b  |N~#A...wcIH{u.I.|
00000120  29 9c 01 b5 64 71 9f ed  68 71 8a 8e 0b 92 7a df  |)...dq..hq....z.|
00000130  c9 df e8 72 ae 9f 98 eb  ec b1 5a 21 ca 49 0d 89  |...r......Z!.I..|
00000140  96 92 a2 49 f8 45 65 8b  e1 39 98 62 1e 72 51 0f  |...I.Ee..9.b.rQ.|
00000150  c5 ba 9d bf 2e 9e 72 4d  31 2e 49 66 72 b2 20 8c  |......rM1.Ifr. .|
00000160  4b 30 7d 47 d9 c2 48 68  e9 ac 81 23 fe f1 3d 08  |K0}G..Hh...#..=.|
00000170  9a 95 11 6e 4a 11 6e e7  c6 60 08 cf ba 66 cf 04  |...nJ.n..`...f..|
00000180  8a 31 c6 06 77 30 a5 92  cf 7f 2a fe e6 19 79 46  |.1..w0....*...yF|
00000190  cd c6 f5 1f 01 ff b2 ac  53 ad f2 d3 2b 71 30 d7  |........S...+q0.|
000001a0  a3 53 8d 40 13 a9 d0 2d  70 2c 06 fd 73 2a 01 f3  |.S.@...-p,..s*..|
000001b0  b0 93 19 32 30 ba f4 40  fa ef 4a cd e0 84 0b 84  |...20..@..J.....|
000001c0  f6 c6 2d 4c 2f aa 5f 39  8f f3 27 02 ca 50 c0 79  |..-L/._9..'..P.y|
000001d0  38 bd a8 0d 72 86 e0 77  26 c5 8b 8e 84 cb 2d 4b  |8...r..w&.....-K|
000001e0  65 4b 92 10 aa a9 d9 93  11 14 34 ef cb d8 e4 94  |eK........4.....|
000001f0  73 fa e0 0a ab b5 c9 ee  cf 15 c4 4f 32 a9 59 68  |s..........O2.Yh|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```[/INDENT]

---

