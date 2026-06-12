---
title: "minimal bash (grub) after running boot-repair"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by paz3 on 2014-05-04
Hello,
I was last running ubuntu 12.04 dual-boot with windows XP before this problem happend: 
When I boot my computer after the BIOS screen I get the command prompt of grub 1.99.
I am unable to get to the normal ubuntu OS.

I've done these operations (chronologically):
[LIST]
[*]Had operational ubuntu 12.04 dual-boot with win XP and all was well. 
[*]Installed a new NVIDIA graphics card. Had trouble with it. 
[*]Installed ubuntu 14.04 instead of the 12.04, and then installed 12.04 again (a couple of times). 
[*]Had trouble with boot - sometimes I had "hd0 out of disk", other times some grub error, and other times ubuntu 12.04 loaded successfully and worked OK. 
[*] Ran boot-repair thinking it would help the non-deterministic boot. 
[*]Current state: when I boot I get a  "minimal bash (grub)" command prompt in which I can type. 
[/LIST]

This is the output of Boot Info Script run using the ubuntu 12.04 liveCD.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

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

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 457366776 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   426,975,231   426,975,169   7 NTFS / exFAT / HPFS
/dev/sda2         426,977,278   488,396,799    61,419,522   5 Extended
/dev/sda5         480,030,720   488,396,799     8,366,080  82 Linux swap / Solaris
/dev/sda6         426,977,280   447,561,727    20,584,448  83 Linux
/dev/sda7         447,563,776   480,022,527    32,458,752  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        10989CD3989CB8A4                       ntfs       
/dev/sda5        17554fb8-462b-4666-84b2-dba91401d9cc   swap       
/dev/sda6        79f985ef-54a9-4cdd-a6ae-5e777e405377   ext4       Storage
/dev/sda7        7cfe4896-1943-4625-b1c3-2c17aa6b1b47   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04.3 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7cfe4896-1943-4625-b1c3-2c17aa6b1b47 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=17554fb8-462b-4666-84b2-dba91401d9cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.8.0-29-generic               1
               =                boot/initrd.img-3.8.0-39-generic               1
               =                boot/vmlinuz-3.8.0-29-generic                  2
               =                boot/vmlinuz-3.8.0-39-generic                  1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1d e8 fd 63 2f 87 52 03  c0 29 ae 7e 8d 9a 06 b7  |...c/.R..).~....|
00000010  ec 38 2c 9b a5 66 70 5e  b2 06 65 45 9d 56 12 6a  |.8,..fp^..eE.V.j|
00000020  54 af 54 b2 3a ae c8 7b  bd 26 ce 64 ed bf 54 36  |T.T.:..{.&.d..T6|
00000030  23 45 8b 28 24 c9 d5 30  5b fc b5 ac 6a 7c 8b 4a  |#E.($..0[...j|.J|
00000040  47 0f 4b 6a cd 9b ec 4f  67 d9 04 b7 94 eb e0 00  |G.Kj...Og.......|
00000050  c6 68 2d e0 a3 76 e6 62  44 d5 ab 70 7e bc 5a b8  |.h-..v.bD..p~.Z.|
00000060  bb a9 15 1d 16 28 66 09  f5 c9 80 8b 44 f9 2a 30  |.....(f.....D.*0|
00000070  02 32 5e 85 61 ef 57 e0  e6 c5 dd d0 21 8c 0f 65  |.2^.a.W.....!..e|
00000080  3f 4f 5c 71 e6 df cd fc  02 20 d6 16 f9 6a 40 0a  |?O\q..... ...j@.|
00000090  f7 c7 62 b8 e7 5c 8c 6b  02 79 d2 f8 b9 8c a1 9c  |..b..\.k.y......|
000000a0  16 3a e8 b4 0b 7a 99 e6  b4 de 9b a5 d3 c3 ee ec  |.:...z..........|
000000b0  a3 4c 1f ec df 31 fa 01  e9 b2 eb 72 4a d6 29 ab  |.L...1.....rJ.).|
000000c0  06 6e a9 d4 a9 d4 35 61  2e 40 eb 6b e3 d2 88 75  |.n....5a.@.k...u|
000000d0  c9 d8 2b 60 30 1c 34 0f  0f ad 6d a7 60 ff 33 9f  |..+`0.4...m.`.3.|
000000e0  08 35 4b 85 ba ed 49 17  7d 76 e7 e8 85 fc 82 a2  |.5K...I.}v......|
000000f0  4a 17 96 af 48 ef da 03  05 a9 75 2b 58 18 6a 13  |J...H.....u+X.j.|
00000100  e6 8a ad 36 c0 18 10 2e  e3 85 15 0e f1 40 77 2b  |...6.........@w+|
00000110  dc 1f 4f 5a 9f ae 28 f3  36 f8 8f 84 cc 0d 95 85  |..OZ..(.6.......|
00000120  47 2a ba 80 fe 1c a3 e4  8d 79 98 26 ad f9 37 28  |G*.......y.&..7(|
00000130  f6 08 f1 a3 4c 20 e8 36  e3 70 8f 97 8b 00 24 b7  |....L .6.p....$.|
00000140  17 ee 9e 8c 37 73 2e 5b  af 11 2a a1 d5 bd aa 5e  |....7s.[..*....^|
00000150  b9 57 af 6b 4e 3c 93 68  a0 85 28 9a a4 b0 88 85  |.W.kN<.h..(.....|
00000160  1b 84 72 fa c1 82 d1 71  ee 91 94 63 58 15 9e 8d  |..r....q...cX...|
00000170  6c 9f 58 27 f8 e4 9d 66  33 3e a7 b3 ce 49 c5 52  |l.X'...f3>...I.R|
00000180  63 3b 22 33 b2 75 15 b8  44 84 4b fb 43 a8 ed 0c  |c;"3.u..D.K.C...|
00000190  4e 48 23 52 30 9f 4f 0c  49 46 59 f9 29 09 a7 5f  |NH#R0.O.IFY.).._|
000001a0  d2 49 75 b2 bf bd 8e 36  47 6c 32 26 2d 44 31 84  |.Iu....6Gl2&-D1.|
000001b0  d9 82 cd 54 84 4b 69 31  6a 29 e2 93 96 70 00 fe  |...T.Ki1j)...p..|
000001c0  ff ff 82 fe ff ff 02 88  29 03 00 a8 7f 00 00 fe  |........).......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 18 3a 01 00 00  |............:...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

Help will be much appreciated.

---

### Post by slooksterpsv on 2014-05-04
If you can get into XP run a chkdsk, if you cant boot off the Live CD again and run
fsck -fy

on your linux drives and ntfs3gfix on the /dev/sda1. Then try to run bootrepair again. Looks like somethings corrupt with the HDD.

---

### Post by slooksterpsv on 2014-05-04
Internet glitched, sorry for the dupe post.

---

### Post by oldfred on 2014-05-04
Did you have nVidia before?
I upgraded my nVidia several years ago and had no issue.
But every new install requires me to add nomodeset on installer boot, and first boot after install or until I install nVidia driver from system settings, software ware & updates and drivers tab.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Unless you have an extremely new nVidia card only install from Ubuntu repository. They now are very new and only the just released cards may need the drivers directly from nVidia or a ppa. And do not over install from a different source. You have to totally purge before installing a different driver.

---

