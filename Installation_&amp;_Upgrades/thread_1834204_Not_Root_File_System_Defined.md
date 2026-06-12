---
title: "Not Root File System Defined"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by DylanEdgar2 on 2011-08-27
First and foremost I am an absolute beginner when it comes to Linux. 

I have recently tried installing Ubuntu 11.04 onto my PC, via a USB as well as using Wubi inside windows 7. Both times I have tried installing, an error message has stopped me stating that 'not root file system is defined'. I have read multiple threads relating to the problem, but as srs5694 has said, I shouldn't try these solutions. I do not mind wiping my whole PC to install Ubuntu. 

Thanks, Dylan

---

### Post by F.G. on 2011-08-27
if it says 'no root filesystem is defined' then is sounds the you need to partition your hard disk, and set one chunk of it to mount as '/'.  this usually a happens in Ubuntu automatically.
when you try to install have you been setting up the partitions manually (if so then you need to set one partition as '/')? or letting the install process do it automatically? if it's automatic it should wipe your whole hard disk and use that.

---

### Post by DylanEdgar2 on 2011-08-27
when installing with Wubi I have no part in the partitioning, everything is done automatically. When installing from a USB Pen drive i have the same issue as the man in this video 

[http://www.youtube.com/watch?v=l5cTNg0gs7A](http://www.youtube.com/watch?v=l5cTNg0gs7A)

it doesn't even allow me to try partitioning the hard drive.

---

### Post by F.G. on 2011-08-27
hmm. that odd.  sorry i can't help. 
I guess when running ubuntu as a live disk you could try partitioning your hd using the gparted utility and then try installing it?
it looks like there's some kind of permission issue, i don't know why that would be though.

---

### Post by Rubi1200 on 2011-08-27
Hi and welcome to the forums DylanEdgar2 :-)

You need to check a few things and answer some questions.

1. in Windows Disk Management are the disks labeled as Dynamic?

2. Do you have a RAID array/was the disk ever part of one?

3. Do/did you have a GPT layout?

You can also post the results of the boot info script to help us troubleshoot this.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by DylanEdgar2 on 2011-08-28
hello Rubi,

1. The disk 'Layout' is 'Simple', the 'Type' is 'Basic', the 'File System' is 'NTFS'. I'm not sure which would be shown as 'Dynamic' so I have stated all three.

2. I do not have a RAID array, or haven't ever had one.

3. Finally, I do not know what a GPT Layout is, sorry.

I am working on getting the Boot Info Script now

---

### Post by DylanEdgar2 on 2011-08-28
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => No known boot loader is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/mapper/nvidia_efaabgaj.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 7355258 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /bootmgr /boot/bcd /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

sdc2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nvidia_efaabgaj1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

nvidia_efaabgaj2: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3990 MB, 3990294528 bytes
255 heads, 63 sectors/track, 485 cylinders, total 7793544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,793,543     7,793,481   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1     ? 1,936,269,394 3,772,285,809 1,836,016,416   7 NTFS / exFAT / HPFS
/dev/sdc2     ? 1,917,848,077 2,462,285,169   544,437,093  73 Unknown
/dev/sdc3     ? 1,818,575,915 2,362,751,050   544,175,136  2b SyllableSecure
/dev/sdc4     ? 2,844,524,554 2,844,579,527        54,974  61 SpeedStor

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc1 overlaps with /dev/sdc4
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc4 ends after the last sector of /dev/sdc

Drive: nvidia_efaabgaj _____________________________________________________________________

Disk /dev/mapper/nvidia_efaabgaj: 1000.2 GB, 1000204861440 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_efaabgaj1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_efaabgaj2            206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0640A77D40A7725B                       ntfs       System Reserved
/dev/sda2        2464A92864A8FDA4                       ntfs       
/dev/sdb1        5930-E222                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ef 66 54 57 00 00 00 00  |.........fTW....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  de c7 7e 04 03 7f 04 f4  |..........~.....|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 07 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BO.TMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

Unknown BootLoader on sdc1


Unknown BootLoader on sdc2

00000000  07 4c be 55 41 9d 67 3b  2e 09 5b cc e7 08 5f f7  |.L.UA.g;..[..._.|
00000010  f9 8e bc 74 28 b0 55 ea  1d 40 25 e1 dc ca c6 dc  |...t(.U..@%.....|
00000020  53 63 c1 c2 f0 41 34 d0  c7 e6 eb e6 0b 23 eb 16  |Sc...A4......#..|
00000030  76 da f5 73 20 69 88 27  db ca 62 4d 5f 89 32 1e  |v..s i.'..bM_.2.|
00000040  7b 48 e0 a8 56 83 a0 64  50 c9 ea 50 00 51 5e ac  |{H..V..dP..P.Q^.|
00000050  04 d7 85 d6 bd 59 aa 29  79 f9 a6 90 83 80 77 89  |.....Y.)y.....w.|
00000060  bd 66 ea ad 5d d8 a6 35  ec c8 d1 62 80 b1 e1 cd  |.f..]..5...b....|
00000070  30 93 2a 1d 9e 4f 6e 97  d6 52 c8 d8 64 0f 6e 71  |0.*..On..R..d.nq|
00000080  99 cb d8 f8 3b 55 ad 5d  ed c9 10 56 21 7e 56 cc  |....;U.]...V!~V.|
00000090  2d 53 e6 17 85 17 9c 0a  b4 83 83 12 bc f1 e6 9c  |-S..............|
000000a0  77 eb 5b bb d3 75 96 32  f9 b7 44 d6 67 e0 f0 f6  |w.[..u.2..D.g...|
000000b0  18 ec b4 29 86 6f 15 32  09 7f 9a df 1f c4 1d 9a  |...).o.2........|
000000c0  f7 47 1f 6c cb 84 71 e9  a5 c5 f4 dc 41 dd 76 28  |.G.l..q.....A.v(|
000000d0  4d 59 9b 83 07 61 c4 74  d1 a0 0e 22 76 33 e2 b4  |MY...a.t..."v3..|
000000e0  28 12 8d fc d6 65 95 a9  b3 cb e4 7a 51 cc 2e a3  |(....e.....zQ...|
000000f0  37 14 5d c8 d0 6e d3 a3  5b 5f d8 7d 1d 8a 04 6e  |7.]..n..[_.}...n|
00000100  83 9d 28 2c 02 04 16 08  1c ca 34 b5 ad 43 d3 d4  |..(,......4..C..|
00000110  1c 37 bb 16 16 68 15 eb  fb 93 a9 f0 53 20 f9 67  |.7...h......S .g|
00000120  a3 fb 4f f0 17 c1 39 00  bf 7a af 20 ce 70 a5 76  |..O...9..z. .p.v|
00000130  10 01 1e ec 54 34 e4 be  35 7b 90 c9 f1 8b ee b0  |....T4..5{......|
00000140  77 c0 96 c8 bb 05 b7 0e  14 b6 eb d5 d4 e2 82 e8  |w...............|
00000150  58 10 66 70 69 a5 ae 20  c2 b8 f2 20 31 40 48 c6  |X.fpi.. ... 1@H.|
00000160  07 e1 0f a2 29 58 57 f1  4c 1c e3 d4 41 80 bc 9e  |....)XW.L...A...|
00000170  e3 26 f3 7b b0 3f 8d 48  4c f4 06 32 a9 52 30 52  |.&.{.?.HL..2.R0R|
00000180  f9 7d 1b 56 9b 88 86 70  ab 0b 6d 9e ee 93 e7 8f  |.}.V...p..m.....|
00000190  7b c7 9f 17 24 76 96 b1  46 18 f5 6e c6 ac 64 4e  |{...$v..F..n..dN|
000001a0  03 84 e0 8d 94 c5 15 ee  56 f7 6d f0 4d b7 99 3e  |........V.m.M..>|
000001b0  3d 5a da d6 b7 08 58 f7  9c d0 82 9f 1e 2e 40 f4  |=Z....X.......@.|
000001c0  02 d2 23 d5 4c 1b 39 c5  f6 e4 11 01 af 58 19 96  |..#.L.9......X..|
000001d0  f5 4a f5 5f f3 f8 19 b2  5e 07 77 f4 3e 21 67 d1  |.J._....^.w.>!g.|
000001e0  30 bc 73 76 45 1d 0c c5  bc d7 55 67 07 64 67 f4  |0.svE.....Ug.dg.|
000001f0  50 4e dd 54 2f 88 fa 2c  72 1e a1 03 c2 a1 9a 40  |PN.T/..,r......@|
00000200

Unknown BootLoader on sdc3

00000000  cc 0b 7f 1e bb aa f1 5b  3c ab 9a a6 27 10 5b 47  |.......[<...'.[G|
00000010  c9 87 bb 68 61 b0 9e ce  4d 39 1b 32 b0 20 19 9d  |...ha...M9.2. ..|
00000020  af 2e 0f 3c bd 75 9f de  b7 cd 9c c9 c5 62 7c 96  |...<.u.......b|.|
00000030  93 05 81 23 01 c9 ac 6f  58 56 5e 13 86 1f 2b f6  |...#...oXV^...+.|
00000040  04 20 9d 2b 10 ac 34 48  c0 50 dc eb 98 e9 53 c6  |. .+..4H.P....S.|
00000050  3d bd b7 25 77 2f 10 48  e2 5b 47 1b 43 9d d6 b3  |=..%w/.H.[G.C...|
00000060  34 d9 b3 c7 f7 26 88 31  31 f9 7e 22 4f 5d 51 69  |4....&.11.~"O]Qi|
00000070  d9 8e 83 b9 5e 88 f0 90  57 04 b1 27 07 07 90 b1  |....^...W..'....|
00000080  65 11 03 b4 13 d1 52 0a  c9 4e 4c 74 32 22 dd 1a  |e.....R..NLt2"..|
00000090  45 6f d2 ac 05 1c ed fa  96 92 76 65 ef cd c8 30  |Eo........ve...0|
000000a0  98 45 78 47 b1 37 fd d3  9d 84 35 a1 c0 0f 0d 9e  |.ExG.7....5.....|
000000b0  ab 2a 1b f9 4e f0 7e 53  cc 9f b1 b6 ad 77 a7 80  |.*..N.~S.....w..|
000000c0  37 87 bd 7f 4c 0b 06 79  7a 52 1d 74 94 d6 2d 83  |7...L..yzR.t..-.|
000000d0  68 db 61 fe 7f e1 3b 2c  b3 56 74 4f 42 58 7a 5b  |h.a...;,.VtOBXz[|
000000e0  af 87 f4 83 23 59 4c 35  4d db 2b db cc ee a8 f8  |....#YL5M.+.....|
000000f0  3b e3 40 8d c3 8b d4 cc  c4 49 c9 bd 75 3f 41 c5  |;.@......I..u?A.|
00000100  e7 a5 7a 30 f7 e5 e9 0f  a6 ef bc 75 82 fd 5d db  |..z0.......u..].|
00000110  93 c8 c4 40 b9 88 f9 27  a1 56 ea 50 8f 4a 6a eb  |...@...'.V.P.Jj.|
00000120  db 18 de 9f af 03 10 6f  a1 45 ba d6 5c 54 da 2c  |.......o.E..\T.,|
00000130  2d 5c 2d eb 63 59 1e c2  f6 df 29 eb 18 07 46 e2  |-\-.cY....)...F.|
00000140  21 f1 9f c8 33 3d 81 65  16 21 90 a4 21 bd 51 0a  |!...3=.e.!..!.Q.|
00000150  07 96 79 c4 42 66 12 ef  2f bb 9b ea cc 52 18 fc  |..y.Bf../....R..|
00000160  ab 59 30 20 1f 0c 47 0b  ba 79 5c 70 9f 43 ff e6  |.Y0 ..G..y\p.C..|
00000170  77 0a f1 12 f0 6f 81 0e  aa f9 65 ec 7c be 91 0d  |w....o....e.|...|
00000180  c0 1c 97 2f 36 d2 a5 5d  5a 52 42 32 98 f2 d0 5a  |.../6..]ZRB2...Z|
00000190  c5 70 c1 fb 3c 00 36 4c  7f 4c f1 cd db 11 11 a0  |.p..<.6L.L......|
000001a0  e5 1c c1 f4 d6 8b 63 56  44 5f 63 45 29 af 48 27  |......cVD_cE).H'|
000001b0  60 db 03 c2 e1 22 f0 82  81 7f ac 69 66 53 1e 04  |`....".....ifS..|
000001c0  5d 31 71 fd 9b ab ad 3f  74 71 cd c4 cb 50 4b 70  |]1q....?tq...PKp|
000001d0  ab ec 46 5f c1 98 ec 4b  fc db 15 77 75 1c bb 38  |..F_...K...wu..8|
000001e0  9b 9f d8 ce 9c a7 51 2c  01 a1 99 78 de e6 6b 5a  |......Q,...x..kZ|
000001f0  00 a4 75 f5 bb 8f 28 47  6d 3e a5 f3 5e 4b 59 d4  |..u...(Gm>..^KY.|
00000200

Unknown BootLoader on sdc4



=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory

---

### Post by dino99 on 2011-08-28
how to install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

