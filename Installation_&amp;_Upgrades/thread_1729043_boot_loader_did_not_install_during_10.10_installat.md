---
title: "boot loader did not install during 10.10 installation"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by yukont on 2011-04-14
I installed netbook ubuntu onto a netbook that had windows 7 on it. I chose the option to install ubuntu alongside my other operating system. at about 3/4 of the way through the installation a message came up stating that I had a boot loader problem (I think it said missing file/could not find file and that I would have to install a boot loader manually.  I then finished the installation and restarted. I had to keep the usb in so it would load. I cant seem to access the internet or start firefox. It has an option to install ubuntu just above the firefox icon. an error message comes up saying ubiquity has crashed

---

### Post by wilee-nilee on 2011-04-14
The alongside method has caused problems, so lets get enough information.

Click on the bootscript link in my signature, and follow the directions on using a live Ubuntu cd to generate a text file. Come back to the thread open a reply and click on the **(#)** in the reply panel, this creates code tags;paste all the text from that generated file between.

---

### Post by yukont on 2011-04-14
oh boy this looks like a lot 





                Boot Info Script 0.55    dated February 15th, 2010                    
   
  ============================= Boot Info Summary: ==============================
   
   => No boot loader is installed in the MBR of /dev/sda
   => Syslinux is installed in the MBR of /dev/sdb
   => Syslinux is installed in the MBR of /dev/sdc
   
  sda1: _________________________________________________________________________
   
      File system:       ext4
      Boot sector type:  -
      Boot sector info:  
      Operating System:  Ubuntu 10.10
      Boot files/dirs:   /etc/fstab
   
  sda2: _________________________________________________________________________
   
      File system:       Extended Partition
      Boot sector type:  Unknown
      Boot sector info:  
   
  sda5: _________________________________________________________________________
   
      File system:       swap
      Boot sector type:  -
      Boot sector info:  
   
  sdb1: _________________________________________________________________________
   
      File system:       vfat
      Boot sector type:  Unknown
      Boot sector info:  No errors found in the Boot Parameter Block.
      Mounting failed:
  mount: /dev/sdb1 already mounted or sdb1 busy
  warning: error reading /etc/mtab: Is a directory
   
  sdc1: _________________________________________________________________________
   
      File system:       vfat
      Boot sector type:  Fat16
      Boot sector info:  No errors found in the Boot Parameter Block.
      Mounting failed:
  mount: /dev/sdb1 already mounted or sdb1 busy
  warning: error reading /etc/mtab: Is a directory
  mount: /dev/sdc1 already mounted or sdc1 busy
  warning: error reading /etc/mtab: Is a directory
   
  =========================== Drive/Partition Info: =============================
   
  Drive: sda ___________________ _____________________________________________________
   
  Disk /dev/sda: 160.0 GB, 160041885696 bytes
  255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
   
  Partition  Boot         Start           End          Size  Id System
   
  /dev/sda1               2,048   306,440,191   306,438,144  83 Linux
  /dev/sda2         306,442,238   312,580,095     6,137,858   5 Extended
  /dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris
   
   
  Drive: sdb ___________________ _____________________________________________________
   
  Disk /dev/sdb: 4051 MB, 4051697664 bytes
  227 heads, 32 sectors/track, 1089 cylinders, total 7913472 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
   
  Partition  Boot         Start           End          Size  Id System
   
  /dev/sdb1    *             32     7,913,471     7,913,440   b W95 FAT32
   
   
  Drive: sdc ___________________ _____________________________________________________
   
  Disk /dev/sdc: 2003 MB, 2003828736 bytes
  42 heads, 41 sectors/track, 2272 cylinders, total 3913728 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
   
  Partition  Boot         Start           End          Size  Id System
   
  /dev/sdc1    *            129     3,913,663     3,913,535   6 FAT16
   
   
  blkid -c /dev/null: ____________________________________________________________
   
  Device           UUID                                   TYPE       LABEL                         
   
  /dev/loop0                                              squashfs                                 
  /dev/loop1       b48e7e10-4e55-e847-9d1c-1cd40bb87e6c   ext2       casper-rw                     
  /dev/sda1        3e70ae3a-7add-4f27-8949-337a83bceeb9   ext4                                     
  /dev/sda2: PTTYPE="dos" 
  /dev/sda5        06157078-c956-4717-be69-83ff8c81daff   swap                                     
  /dev/sda: PTTYPE="dos" 
  /dev/sdb1        640A-CF99                              vfat       PENDRIVE                      
  /dev/sdb: PTTYPE="dos" 
  /dev/sdc1        9814-452E                              vfat       MICRO SD                      
  /dev/sdc: PTTYPE="dos" 
   
  ============================ "mount | grep ^/dev  output: ===========================
   
  Device           Mount_Point              Type       Options
   
   
   
  =============================== sda1/etc/fstab: ===============================
   
  # /etc/fstab: static file system information.
  #
  # Use 'blkid -o value -s UUID' to print the universally unique identifier
  # for a device; this may be used with UUID= as a more robust way to name
  # devices that works even if disks are added and removed. See fstab(5).
  #
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc            /proc           proc    nodev,noexec,nosuid 0       0
  # / was on /dev/sda1 during installation
  UUID=3e70ae3a-7add-4f27-8949-337a83bceeb9 /               ext4    errors=remount-ro 0       1
  /dev/sda5       none            swap    sw              0       0
   
  =================== sda1: Location of files loaded by Grub: ===================
   
   
     1.1GB: boot/initrd.img-2.6.35-22-generic
    94.6GB: boot/vmlinuz-2.6.35-22-generic
     1.1GB: initrd.img
    94.6GB: vmlinuz
  =========================== Unknown MBRs/Boot Sectors/etc =======================
   
  Unknown BootLoader  on sda2
   
  00000000  b7 f0 6c fb c1 69 86 4f  0d 19 aa 04 28 dd 22 04  |..l..i.O....(.".|
  00000010  b5 a7 95 2e d7 b7 b1 79  fd 2f f7 36 2d 10 9a 0b  |.......y./.6-...|
  00000020  5f 01 b5 bb 11 b0 75 bb  41 6f 2d ce 7c 83 4f 3a  |_.....u.Ao-.|.O:|
  00000030  43 24 d1 e7 b5 f3 48 5b  f6 4d 39 18 2e 0e d0 f4  |C$....H[.M9.....|
  00000040  eb 8e f9 85 c8 55 34 29  d2 4e 5b c2 9c b6 47 57  |.....U4).N[...GW|
  00000050  0e 68 38 12 72 ff 8e b9  e6 8c 66 d4 29 3e e7 24  |.h8.r.....f.)>.$|
  00000060  34 62 a9 dd 09 e5 9a 31  0a 60 b7 02 77 54 7e f2  |4b.....1.`..wT~.|
  00000070  13 f7 1e 5a 6c d5 1b 52  f1 8d 5d d8 ea 5a 02 a8  |...Zl..R..]..Z..|
  00000080  06 00 82 0e eb 8b f3 2d  13 11 8c 16 5b 36 97 e9  |.......-....[6..|
  00000090  16 c7 53 5e b0 33 fd 25  8e 8f 61 0f 8f 53 57 72  |..S^.3.%..a..SWr|
  000000a0  01 18 4c 2f 8d 84 60 d5  6d 92 70 4c 18 2c d6 27  |..L/..`.m.pL.,.'|
  000000b0  23 d6 38 32 38 01 8d ef  8e de 10 85 e1 f3 af 02  |#.828...........|
  000000c0  d4 e9 cd d7 09 57 7e 2f  7d e3 91 4f 5e 4a 58 aa  |.....W~/}..O^JX.|
  000000d0  5f dd 0a c0 b5 eb 26 06  0d 25 ec e6 06 5e f0 6e  |_.....&..%...^.n|
  000000e0  d2 36 69 35 93 da 66 e8  33 84 d6 2b e8 22 40 25  |.6i5..f.3..+."@%|
  000000f0  e4 be 16 c4 af 09 d8 2f  a6 c0 5c 6e f6 a9 92 e6  |......./..\n....|
  00000100  96 e3 ba 00 fa cc 02 58  e0 4b 30 87 f5 03 24 4f  |.......X.K0...$O|
  00000110  e1 52 c5 17 ef ee f2 a3  7c 18 c1 03 2c 4f e3 54  |.R......|...,O.T|
  00000120  06 3b d5 c5 eb d7 f9 c6  1b e3 34 6b 34 df f7 df  |.;........4k4...|
  00000130  79 92 e6 74 61 63 e3 d2  fd 7c c0 69 f8 69 81 76  |y..tac...|.i.i.v|
  00000140  e3 a2 7e f0 63 84 57 b8  f9 ad fb 3c 69 fd 6b f6  |..~.c.W....<i.k.|
  00000150  3b 7a 07 db bc 6c 57 a1  0c df bb fe bd 36 47 05  |;z...lW......6G.|
  00000160  16 c4 e9 61 ce e9 91 6e  af 90 ea 40 7b 4f ef 43  |...a...n...@{O.C|
  00000170  1f eb 28 5e 6d d4 7a f3  98 e5 a5 9b f4 ae 30 dc  |..(^m.z.......0.|
  00000180  22 40 04 cd 8c d9 4b df  06 37 f8 95 90 bb b2 a7  |"@....K..7......|
  00000190  7b fd b9 3b 18 88 3f af  04 fc 24 84 55 16 e5 5e  |{..;..?...$.U..^|
  000001a0  c8 56 82 a7 bd b7 64 1e  01 64 02 11 3e ea 5d c5  |.V....d..d..>.].|
  000001b0  51 50 0e 18 da b7 aa 3e  34 86 f3 4b c6 d9 00 fe  |QP.....>4..K....|
  000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
  000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
  *
  000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
  00000200
   
  Unknown BootLoader  on sdb1
   
  00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c0 03  |.X.SYSLINUX.....|
  00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
  00000020  e0 bf 78 00 20 1e 00 00  00 00 00 00 02 00 00 00  |..x. ...........|
  00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
  00000040  80 00 29 99 cf 0a 64 4e  4f 20 4e 41 4d 45 20 20  |..)...dNO NAME  |
  00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
  00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
  00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
  00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
  00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
  000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
  000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
  000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
  000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
  000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
  000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
  00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
  00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
  00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
  00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
  00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
  00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
  00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
  00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
  00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
  00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
  000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
  000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
  000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
  000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
  000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
  000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
  00000200
   
   
  =============================== StdErr Messages: ===============================
   
  warning: error reading /etc/mtab: Is a directory
  warning: error reading /etc/mtab: Is a directory
  warning: error reading /etc/mtab: Is a directory
  warning: error reading /etc/mtab: Is a directory
  warning: error reading /etc/mtab: Is a directory
  warning: error reading /etc/mtab: Is a directory
  warning: error reading /etc/mtab: Is a directory

---

### Post by wilee-nilee on 2011-04-14
/dev/sda1 2,048 306,440,191 306,438,144 83 Linux
/dev/sda2 306,442,238 312,580,095 6,137,858 5 Extended
/dev/sda5 306,442,240 312,580,095 6,137,856 82 Linux swap / Solaris

I think by chosing the install alongside another, it over wrote the whole hard drive. 

Testdisk is a utility people use to recover partitiopns and stuff, hard to say how it will work here, I'm not real familiar with it, but that's what I see most often suggested.

Here is a link to look at I suspect you will get some more help at least I hope so looking at the test disk info may help.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Just for the others looking.```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> No boot loader is installed in the MBR of /dev/sda
=> Syslinux is installed in the MBR of /dev/sdb
=> Syslinux is installed in the MBR of /dev/sdc

sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.10
Boot files/dirs: /etc/fstab

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy
warning: error reading /etc/mtab: Is a directory

sdc1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy
warning: error reading /etc/mtab: Is a directory
mount: /dev/sdc1 already mounted or sdc1 busy
warning: error reading /etc/mtab: Is a directory

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 2,048 306,440,191 306,438,144 83 Linux
/dev/sda2 306,442,238 312,580,095 6,137,858 5 Extended
/dev/sda5 306,442,240 312,580,095 6,137,856 82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 4051 MB, 4051697664 bytes
227 heads, 32 sectors/track, 1089 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 * 32 7,913,471 7,913,440 b W95 FAT32


Drive: sdc ___________________ __________________________________________________ ___

Disk /dev/sdc: 2003 MB, 2003828736 bytes
42 heads, 41 sectors/track, 2272 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdc1 * 129 3,913,663 3,913,535 6 FAT16


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/loop1 b48e7e10-4e55-e847-9d1c-1cd40bb87e6c ext2 casper-rw
/dev/sda1 3e70ae3a-7add-4f27-8949-337a83bceeb9 ext4
/dev/sda2: PTTYPE="dos"
/dev/sda5 06157078-c956-4717-be69-83ff8c81daff swap
/dev/sda: PTTYPE="dos"
/dev/sdb1 640A-CF99 vfat PENDRIVE
/dev/sdb: PTTYPE="dos"
/dev/sdc1 9814-452E vfat MICRO SD
/dev/sdc: PTTYPE="dos"

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options



=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=3e70ae3a-7add-4f27-8949-337a83bceeb9 / ext4 errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0

=================== sda1: Location of files loaded by Grub: ===================


1.1GB: boot/initrd.img-2.6.35-22-generic
94.6GB: boot/vmlinuz-2.6.35-22-generic
1.1GB: initrd.img
94.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda2

00000000 b7 f0 6c fb c1 69 86 4f 0d 19 aa 04 28 dd 22 04 |..l..i.O....(.".|
00000010 b5 a7 95 2e d7 b7 b1 79 fd 2f f7 36 2d 10 9a 0b |.......y./.6-...|
00000020 5f 01 b5 bb 11 b0 75 bb 41 6f 2d ce 7c 83 4f 3a |_.....u.Ao-.|.O
00000030 43 24 d1 e7 b5 f3 48 5b f6 4d 39 18 2e 0e d0 f4 |C$....H[.M9.....|
00000040 eb 8e f9 85 c8 55 34 29 d2 4e 5b c2 9c b6 47 57 |.....U4).N[...GW|
00000050 0e 68 38 12 72 ff 8e b9 e6 8c 66 d4 29 3e e7 24 |.h8.r.....f.)>.$|
00000060 34 62 a9 dd 09 e5 9a 31 0a 60 b7 02 77 54 7e f2 |4b.....1.`..wT~.|
00000070 13 f7 1e 5a 6c d5 1b 52 f1 8d 5d d8 ea 5a 02 a8 |...Zl..R..]..Z..|
00000080 06 00 82 0e eb 8b f3 2d 13 11 8c 16 5b 36 97 e9 |.......-....[6..|
00000090 16 c7 53 5e b0 33 fd 25 8e 8f 61 0f 8f 53 57 72 |..S^.3.%..a..SWr|
000000a0 01 18 4c 2f 8d 84 60 d5 6d 92 70 4c 18 2c d6 27 |..L/..`.m.pL.,.'|
000000b0 23 d6 38 32 38 01 8d ef 8e de 10 85 e1 f3 af 02 |#.828...........|
000000c0 d4 e9 cd d7 09 57 7e 2f 7d e3 91 4f 5e 4a 58 aa |.....W~/}..O^JX.|
000000d0 5f dd 0a c0 b5 eb 26 06 0d 25 ec e6 06 5e f0 6e |_.....&..%...^.n|
000000e0 d2 36 69 35 93 da 66 e8 33 84 d6 2b e8 22 40 25 |.6i5..f.3..+."@%|
000000f0 e4 be 16 c4 af 09 d8 2f a6 c0 5c 6e f6 a9 92 e6 |......./..\n....|
00000100 96 e3 ba 00 fa cc 02 58 e0 4b 30 87 f5 03 24 4f |.......X.K0...$O|
00000110 e1 52 c5 17 ef ee f2 a3 7c 18 c1 03 2c 4f e3 54 |.R......|...,O.T|
00000120 06 3b d5 c5 eb d7 f9 c6 1b e3 34 6b 34 df f7 df |.;........4k4...|
00000130 79 92 e6 74 61 63 e3 d2 fd 7c c0 69 f8 69 81 76 |y..tac...|.i.i.v|
00000140 e3 a2 7e f0 63 84 57 b8 f9 ad fb 3c 69 fd 6b f6 |..~.c.W....<i.k.|
00000150 3b 7a 07 db bc 6c 57 a1 0c df bb fe bd 36 47 05 |;z...lW......6G.|
00000160 16 c4 e9 61 ce e9 91 6e af 90 ea 40 7b 4f ef 43 |...a...n...@{O.C|
00000170 1f eb 28 5e 6d d4 7a f3 98 e5 a5 9b f4 ae 30 dc |..(^m.z.......0.|
00000180 22 40 04 cd 8c d9 4b df 06 37 f8 95 90 bb b2 a7 |"@....K..7......|
00000190 7b fd b9 3b 18 88 3f af 04 fc 24 84 55 16 e5 5e |{..;..?...$.U..^|
000001a0 c8 56 82 a7 bd b7 64 1e 01 64 02 11 3e ea 5d c5 |.V....d..d..>.].|
000001b0 51 50 0e 18 da b7 aa 3e 34 86 f3 4b c6 d9 00 fe |QP.....>4..K....|
000001c0 ff ff 82 fe ff ff 02 00 00 00 00 a8 5d 00 00 00 |............]...|
000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200

Unknown BootLoader on sdb1

00000000 eb 58 90 53 59 53 4c 49 4e 55 58 00 02 08 c0 03 |.X.SYSLINUX.....|
00000010 02 00 00 00 00 f8 00 00 3f 00 ff 00 20 00 00 00 |........?... ...|
00000020 e0 bf 78 00 20 1e 00 00 00 00 00 00 02 00 00 00 |..x. ...........|
00000030 01 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000040 80 00 29 99 cf 0a 64 4e 4f 20 4e 41 4d 45 20 20 |..)...dNO NAME |
00000050 20 20 46 41 54 33 32 20 20 20 fa fc 31 c9 8e d1 | FAT32 ..1...|
00000060 bc 76 7b 52 06 57 1e 56 8e c1 b1 26 bf 78 7b f3 |.v{R.W.V...&.x{.|
00000070 a5 8e d9 bb 78 00 0f b4 37 0f a0 56 20 d2 78 1b |....x...7..V .x.|
00000080 31 c0 b1 06 89 3f 89 47 02 f3 64 a5 8a 0e 18 7c |1....?.G..d....||
00000090 88 4d bc 50 50 50 50 cd 13 eb 5c 8b 55 aa 8b 75 |.M.PPPP...\.U..u|
000000a0 a8 c1 ee 04 01 f2 81 fa b7 07 73 2b f6 45 b4 7f |..........s+.E..|
000000b0 75 25 38 4d b8 74 20 66 3d 21 47 50 54 75 10 80 |u%8M.t f=!GPTu..|
000000c0 7d b8 ed 75 0a 66 ff 75 ec 66 ff 75 e8 eb 0f 51 |}..u.f.u.f.u...Q|
000000d0 51 66 ff 75 bc eb 07 51 51 66 ff 36 1c 7c b4 08 |Qf.u...QQf.6.|..|
000000e0 cd 13 72 13 20 e4 75 0f c1 ea 08 42 89 16 1a 7c |..r. .u....B...||
000000f0 83 e1 3f 89 0e 18 7c fb bb aa 55 b4 41 8a 16 74 |..?...|...U.A..t|
00000100 7b cd 13 72 10 81 fb 55 aa 75 0a f6 c1 01 74 05 |{..r...U.u....t.|
00000110 c6 06 45 7d 00 66 b8 08 40 00 00 66 ba 00 00 00 |..E}.f..@..f....|
00000120 00 bb 00 7e e8 10 00 66 81 3e 24 7e d4 ff 73 72 |...~...f.>$~..sr|
00000130 75 76 ea 38 7e 00 00 66 03 06 60 7b 66 13 16 64 |uv.8~..f..`{f..d|
00000140 7b b9 10 00 eb 2b 66 52 66 50 06 53 6a 01 6a 10 |{....+fRfP.Sj.j.|
00000150 89 e6 66 60 b4 42 e8 7f 00 66 61 8d 64 10 72 01 |..f`.B...fa.d.r.|
00000160 c3 66 60 31 c0 e8 70 00 66 61 e2 da c6 06 45 7d |.f`1..p.fa....E}|
00000170 2b 66 60 66 0f b7 36 18 7c 66 0f b7 3e 1a 7c 66 |+f`f..6.|f..>.|f|
00000180 f7 f6 31 c9 87 ca 66 f7 f7 66 3d ff 03 00 00 77 |..1...f..f=....w|
00000190 17 c0 e4 06 41 08 e1 88 c5 88 d6 b8 01 02 e8 37 |....A..........7|
000001a0 00 66 61 72 01 c3 e2 c9 31 f6 8e d6 bc 68 7b 8e |.far....1....h{.|
000001b0 de 66 8f 06 78 00 be df 7d e8 09 00 31 c0 cd 16 |.f..x...}...1...|
000001c0 cd 19 f4 eb fd 66 60 ac 20 c0 74 09 b4 0e bb 07 |.....f`. .t.....|
000001d0 00 cd 10 eb f2 66 61 c3 8a 16 74 7b cd 13 c3 42 |.....fa...t{...B|
000001e0 6f 6f 74 20 65 72 72 6f 72 0d 0a 00 00 00 00 00 |oot error.......|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


=============================== StdErr Messages: ===============================

warning: error reading /etc/mtab: Is a directory
warning: error reading /etc/mtab: Is a directory
warning: error reading /etc/mtab: Is a directory
warning: error reading /etc/mtab: Is a directory
warning: error reading /etc/mtab: Is a directory
warning: error reading /etc/mtab: Is a directory
warning: error reading /etc/mtab: Is a directory
```

---

### Post by yukont on 2011-04-14
test disc has about 4 options for linux which one should I use?

---

### Post by wilee-nilee on 2011-04-14
> **yukont said:**
> test disc has about 4 options for linux which one should I use?

Personally I don't know, I would suggest waiting for more help.

---

