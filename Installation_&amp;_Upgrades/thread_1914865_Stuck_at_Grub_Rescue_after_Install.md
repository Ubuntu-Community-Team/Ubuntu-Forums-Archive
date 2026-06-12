---
title: "Stuck at Grub Rescue after Install"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by Jonnyboy678 on 2012-01-25
Hi Folks, got myself in a bit of a pickle here!! Absolute begginer to Ubuntu so hope you can help, I'll list my problem and the current steps I have taken so far.
 
Installed Ubuntu last night using WUBI. Initially I was getting error message when this was completing so copied the ISO image and Wubi.exe into a brand new partition I had created on my hard drive and ran it that way. 
 
Install completed and asked me to re-boot. I ok'd that message and when it ran through the reboot I'm now stuck on the Grub Rescue> prompt.
 
Spent about 3 hours this morning reading threads on here but can't get a solution that works for me.
 
I'm using a netbook therefore no CD-rom drive. I can however get into a windows command prompt by going through the Samsung recovery centre when I hit F10 when booting up and also get into the BIOS. 
 
Can anyone help me get past the Grub Rescue prompt so that I can get back into Windows 7.
 
If you need any more information let me know and i'll provide it.
 
Thanks

---

### Post by raja.genupula on 2012-01-25
Hey in my signature there link named as Grub restore .using that install Boot-Repair in live cd mode and restore the GRUB . It will be fine , I am sure .All the best .

---

### Post by Jonnyboy678 on 2012-01-25
> **raja.genupula said:**
> Hey in my signature there link named as Grub restore .using that install Boot-Repair in live cd mode and restore the GRUB . It will be fine , I am sure .All the best .
 
Thanks for the response but I don't have a cd drive on my netbook.  Is there another way to run this?

---

### Post by raja.genupula on 2012-01-25
make Live USB . 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

That will help you . All the best.

---

### Post by Jonnyboy678 on 2012-01-25
Ok , thanks will give it a try when i get in tonight

---

### Post by Jonnyboy678 on 2012-01-26
Ok still having problems with this.  I've downloaded Ubuntu onto a USB drive and changed the BIOS to boot from this.  That works OK and I'm able to boot into Ubuntu and access terminal etc.
 
However, I've not been able to get either Boot Info Script or grub recovery to sucessfully run.  Is it possible that my original install of Ubuntu didn't complete properly and if so could i try to re-install it from the USB??
 
Thanks

---

### Post by darkod on 2012-01-26
First of all, STOP.
The steps to troubleshoot boot problems are not the same for wubi and for dual boot install.

When you boot the computer, do you get the windows bootloader or immediately the boot error?

With wubi you should get the windows bootloader (not grub), with option for windows and ubuntu. Only when you select ubuntu, the wubi (virtual ubuntu) starts loading and might show a grub menu or grub error.

When exactly do you get the error?

---

### Post by Jonnyboy678 on 2012-01-26
Hi Darkod.
 
As soon as I boot the computer up I get a grub rescue prompt. this has happened from the first time I installed Ubuntu. When I installed it the other night, it completed the download of files, I specified where to put them and entered a user name and password on the screen and it then asked to restart to complete the installation. It was at this point the Grub Rescue prompt appeared.

---

### Post by darkod on 2012-01-26
Sounds like something went wrong. But it would be really nice if you can run the boot info script. Boot with the usb in live mode (Try Ubuntu), connect to internet (wired connection should work almost always, wireless depends), and follow the link in my signature to download and run the boot info script. There are instructions there how to run it and post the results.

Watch out where you download and unpack it, the command to run it should reflect the correct path. Also watch out that linux makes difference between capital letters and small case, it's not like windows. When you type the path, Downloads is not the same as downloads. I say this because it would usually download in Downloads and if you unpack it there you can run it from there. Note that the folder name is Downloads.

---

### Post by Jonnyboy678 on 2012-01-26
Ok, I managed to run the boot info script, and results are as attached
 
```

Boot Info Script 0.60 from 17 May 2011
&#12288;
============================= Boot Info Summary: ===============================
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for on this drive.
=> Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
sda1: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: /bootmgr /boot/bcd /boot/grub/core.img
sda2: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: /bootmgr /Boot/BCD
sda3: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe /wubildr /wubildr.mbr
sda4: __________________________________________________________________________
File system: Extended Partition
Boot sector type: -
Boot sector info: 
sda5: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: According to the info in the boot sector, sda5 starts 
at sector 63.
Operating System: 
Boot files: 
sda6: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda6 starts 
at sector 63.
Operating System: 
Boot files: /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
/ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
/boot/grub/core.img
sda6/Wubi: _____________________________________________________________________
File system: 
Boot sector type: Unknown
Boot sector info: 
Mounting failed: mount: unknown filesystem type ''
sda7: __________________________________________________________________________
File system: vfat
Boot sector type: Unknown
Boot sector info: According to the info in the boot sector, sda7 starts 
at sector 0. But according to the info from fdisk, 
sda7 starts at sector 479195136. According to the info 
in the boot sector, sda7 has 0 sectors.
Operating System: 
Boot files: /grub/grub.cfg /grub/core.img
sdb1: __________________________________________________________________________
File system: vfat
Boot sector type: SYSLINUX 4.05 2011-12-09
Boot sector info: Syslinux looks at sector 108288 of /dev/sdb1 for its 
second stage. SYSLINUX is installed in the directory. 
The integrity check of the ADV area failed. No errors 
found in the Boot Parameter Block.
Operating System: 
Boot files: /syslinux/syslinux.cfg /ldlinux.sys
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sda1 2,048 31,459,327 31,457,280 27 Hidden NTFS (Recovery Environment)
/dev/sda2 * 31,459,328 31,664,127 204,800 7 NTFS / exFAT / HPFS
/dev/sda3 31,664,128 136,710,143 105,046,016 7 NTFS / exFAT / HPFS
/dev/sda4 136,710,144 488,392,064 351,681,921 f W95 Extended (LBA)
/dev/sda5 136,712,192 347,453,819 210,741,628 7 NTFS / exFAT / HPFS
/dev/sda6 347,453,883 479,186,819 131,732,937 7 NTFS / exFAT / HPFS
/dev/sda7 479,195,136 488,392,064 9,196,929 49 Unknown
&#12288;
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sdb1 * 32 7,821,311 7,821,280 b W95 FAT32
&#12288;
"blkid" output: ________________________________________________________________
Device UUID TYPE LABEL
/dev/loop0 squashfs 
/dev/sda1 361C0AC01C0A7ADF ntfs RECOVERY
/dev/sda2 0E220BBD220BA933 ntfs SYSTEM
/dev/sda3 A8DC0E05DC0DCF0E ntfs 
/dev/sda5 01CCDAC75E871580 ntfs 
/dev/sda6 01CCDAC7622068E0 ntfs Ubuntu
/dev/sda7 4B13-E037 vfat 
/dev/sdb1 54F2-021E vfat PENDRIVE
================================ Mount points: =================================
Device Mount_Point Type Options
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sda2 /media/SYSTEM fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3 /media/A8DC0E05DC0DCF0E fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 /media/01CCDAC75E871580 fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 /cdrom vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
&#12288;
=================== sda1: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
?? = ?? boot/grub/core.img 1
=================== sda6: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
?? = ?? boot/grub/core.img 1
============================= sda7/grub/grub.cfg: ==============================
--------------------------------------------------------------------------------
#
# grub.cfg for a simple text menu.
# In the current architecture, this always just boots hyperspace.
# see normal/main.c
#
set quietmenu=1
set default=0
set timeout=0
menuentry "Hypercore" {
sethsroot
psaloader psa0
}
--------------------------------------------------------------------------------
=================== sda7: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
?? = ?? grub/core.img 1
?? = ?? grub/grub.cfg 1
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
GiB - GB File Fragment(s)
?? = ?? ldlinux.sys 1
?? = ?? syslinux/chain.c32 1
?? = ?? syslinux/gfxboot.c32 1
?? = ?? syslinux/syslinux.cfg 1
?? = ?? syslinux/vesamenu.c32 1
============== sdb1: Version of COM32(R) files used by Syslinux: ===============
syslinux/chain.c32 : COM32R module (v4.xx)
syslinux/gfxboot.c32 : COM32R module (v4.xx)
syslinux/vesamenu.c32 : COM32R module (v4.xx)
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda6/Wubi
00000000 30 30 30 30 30 30 30 30 30 30 30 30 30 30 30 30 |0000000000000000|
*
00000200
Unknown BootLoader on sda7
00000000 eb 4b 90 6d 6b 64 6f 73 66 73 00 00 02 04 3f 00 |.K.mkdosfs....?.|
00000010 02 00 02 00 10 f8 03 00 20 00 40 00 00 00 00 00 |........ .@.....|
00000020 00 00 00 00 00 00 29 37 e0 13 4b 20 20 20 20 20 |......)7..K |
00000030 20 20 20 20 20 20 46 41 54 31 32 20 20 20 04 00 | FAT12 ..|
00000040 00 80 00 08 01 f0 8f 1c 00 00 00 00 80 fa eb 07 |................|
00000050 f6 c2 80 75 02 b2 80 ea 5c 7c 00 00 31 c0 8e d8 |...u....\|..1...|
00000060 8e d0 bc 00 20 fb a0 4c 7c 3c ff 74 02 88 c2 52 |.... ..L|<.t...R|
00000070 be 71 7d e8 23 01 be 05 7c f6 c2 80 74 48 b4 41 |.q}.#...|...tH.A|
00000080 bb aa 55 cd 13 5a 52 72 3d 81 fb 55 aa 75 37 83 |..U..ZRr=..U.u7.|
00000090 e1 01 74 32 31 c0 89 44 04 40 88 44 ff 89 44 02 |..t21..D.@.D..D.|
000000a0 c7 04 10 00 66 8b 1e 44 7c 66 89 5c 08 66 8b 1e |....f..D|f.\.f..|
000000b0 48 7c 66 89 5c 0c c7 44 06 00 70 b4 42 cd 13 72 |H|f.\..D..p.B..r|
000000c0 05 bb 00 70 eb 73 b4 08 cd 13 73 0a f6 c2 80 0f |...p.s....s.....|
000000d0 84 f0 00 e9 83 00 66 0f b6 c6 88 64 ff 40 66 89 |......f....d.@f.|
000000e0 44 04 0f b6 d1 c1 e2 02 88 e8 88 f4 40 89 44 08 |D...........@.D.|
000000f0 0f b6 c2 c0 e8 02 66 89 04 66 a1 48 7c 66 09 c0 |......f..f.H|f..|
00000100 75 4f 66 a1 44 7c 66 31 d2 66 f7 34 88 d1 31 d2 |uOf.D|f1.f.4..1.|
00000110 66 f7 74 04 3b 44 08 7d 38 fe c1 88 c5 30 c0 c1 |f.t.;D.}8....0..|
00000120 e8 02 08 c1 88 d0 5a 88 c6 bb 00 70 8e c3 31 db |......Z....p..1.|
00000130 b8 01 02 cd 13 72 2a 8c c3 8e 06 42 7c 60 1e b9 |.....r*....B|`..|
00000140 00 01 8e db 31 f6 31 ff fc f3 a5 1f 61 ff 26 40 |....1.1.....a.&@|
00000150 7c be 77 7d e8 42 00 eb 0e be 7c 7d e8 3a 00 eb ||.w}.B....|}.:..|
00000160 06 be 86 7d e8 32 00 be 8b 7d e8 2c 00 cd 18 eb |...}.2...}.,....|
00000170 fe 00 00 00 00 00 00 47 65 6f 6d 00 48 61 72 64 |.......Geom.Hard|
00000180 20 44 69 73 6b 00 52 65 61 64 00 20 45 72 72 6f | Disk.Read. Erro|
00000190 72 00 bb 01 00 b4 0e cd 10 ac 3c 00 75 f4 c3 00 |r.........<.u...|
000001a0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001b0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 24 12 |..............$.|
000001c0 0f 09 00 be bd 7d 31 c0 cd 13 46 8a 0c 80 f9 00 |.....}1...F.....|
000001d0 75 0f be da 7d e8 c1 ff eb 8d 46 6c 6f 70 70 79 |u...}.....Floppy|
000001e0 00 bb 00 70 b8 01 02 b5 00 b6 00 cd 13 72 d7 b6 |...p.........r..|
000001f0 01 b5 4f e9 e0 fe 00 00 00 00 00 00 00 00 55 aa |..O...........U.|
00000200
&#12288;
=============================== StdErr Messages: ===============================
unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
&#12288;

```

---

### Post by darkod on 2012-01-26
I don't work with wubi so I don't have an exact idea what should be where.

One thing is for sure, you DO have grub2 on the MBR of the disk and it shouldn't be there.

Also the wubildr and wubildr.mbr files on /dev/sda3 I am not sure if they should be there. Or they are remains of the first failed wubi install. Because you have other /ubuntu/winboot/wubildr and wubildr.mbr on /dev/sda6 which seems to be your latest wubi install.

First to remove grub2 from the MBR. If you have a win7 install disc or a rescue disc, you can boot with it and do a repair.
If not, you can install basic bootloader from ubuntu live mode which can boot windows. To do this, open terminal and execute:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Note: It will give you some warning about the lilo config file that will sound scary. Ignore it, it's normal. Just continue with the lilo install.
Restart and you should get your windows bootloader. Whether it will have an option to boot wubi (and whether it will work or not), I don't know right now. Lets see.

Later we will worry about some files that look redundant. Also check if windows will boot if you get the windows bootloader to show up.

---

### Post by Jonnyboy678 on 2012-01-26
Ok tried to install Lilo but got the following error
 
```

[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ sudo apt-get install lilo[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Reading package lists... Done[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Building dependency tree       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Reading state information... Done[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Suggested packages:[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] lilo-doc[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]The following NEW packages will be installed:[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] lilo[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Need to get 277 kB of archives.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]After this operation, 827 kB of additional disk space will be used.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Err http://archive.ubuntu.com/ubuntu/ oneiric/main lilo i386 1:23.2-2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] Could not resolve 'archive.ubuntu.com'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_23.2-2_i386.deb  Could not resolve 'archive.ubuntu.com'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/FONT][/SIZE]

```
 
Do i need to be connected to the internet for this as I'm not currently. Also if it's easier I can get to a command prompt through the Samsung recovery centre on my netbook, so not sure if i could do anything from there.
 
 
EDIT - You know what I've just noticed the http:// in the request so I obviously do need to be online.  I'll try this tongiht when I get home as no net access here at work.

---

### Post by darkod on 2012-01-26
Yeap, you got it. It needs internet it install from the online repositories.

---

### Post by Jonnyboy678 on 2012-01-27
Ok, I ran lilo last night and it completed fine, however on a reboot it just went straight back to the Grub Rescue Prompt.  Any ideas what I should try next.

---

### Post by Jonnyboy678 on 2012-01-29
Just bumping this to see if anyone has any suggestions before I have to think about reformatting to get my pc back up and running.

---

### Post by darkod on 2012-01-29
1. Do you get the windows bootloader now (before any grub rescue) or not?

2. Run the boot info script again and post the results.

---

### Post by Jonnyboy678 on 2012-01-29
> **darkod said:**
> 1. Do you get the windows bootloader now (before any grub rescue) or not?

2. Run the boot info script again and post the results.

Hi,
No bootloader at all

re-ran the boot info script again and these are the results.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda6/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 479195136. According to the info 
                       in the boot sector, sda7 has 0 sectors.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 108288 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   136,710,143   105,046,016   7 NTFS / exFAT / HPFS
/dev/sda4         136,710,144   488,392,064   351,681,921   f W95 Extended (LBA)
/dev/sda5         136,712,192   347,453,819   210,741,628   7 NTFS / exFAT / HPFS
/dev/sda6         347,453,883   479,186,819   131,732,937   7 NTFS / exFAT / HPFS
/dev/sda7         479,195,136   488,392,064     9,196,929  49 Unknown


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        361C0AC01C0A7ADF                       ntfs       RECOVERY
/dev/sda2        0E220BBD220BA933                       ntfs       SYSTEM
/dev/sda3        A8DC0E05DC0DCF0E                       ntfs       
/dev/sda5        01CCDAC75E871580                       ntfs       
/dev/sda6        01CCDAC7622068E0                       ntfs       Ubuntu
/dev/sda7        4B13-E037                              vfat       
/dev/sdb1        54F2-021E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

============================= sda7/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# grub.cfg for a simple text menu.
# In the current architecture, this always just boots hyperspace.
# see normal/main.c
#
set quietmenu=1
set default=0
set timeout=0

menuentry "Hypercore" {
         sethsroot
         psaloader psa0
}
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1

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
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda6/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sda7

00000000  eb 4b 90 6d 6b 64 6f 73  66 73 00 00 02 04 3f 00  |.K.mkdosfs....?.|
00000010  02 00 02 00 10 f8 03 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 00 00 29 37  e0 13 4b 20 20 20 20 20  |......)7..K     |
00000030  20 20 20 20 20 20 46 41  54 31 32 20 20 20 04 00  |      FAT12   ..|
00000040  00 80 00 08 01 f0 8f 1c  00 00 00 00 80 fa eb 07  |................|
00000050  f6 c2 80 75 02 b2 80 ea  5c 7c 00 00 31 c0 8e d8  |...u....\|..1...|
00000060  8e d0 bc 00 20 fb a0 4c  7c 3c ff 74 02 88 c2 52  |.... ..L|<.t...R|
00000070  be 71 7d e8 23 01 be 05  7c f6 c2 80 74 48 b4 41  |.q}.#...|...tH.A|
00000080  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
00000090  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000a0  c7 04 10 00 66 8b 1e 44  7c 66 89 5c 08 66 8b 1e  |....f..D|f.\.f..|
000000b0  48 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |H|f.\..D..p.B..r|
000000c0  05 bb 00 70 eb 73 b4 08  cd 13 73 0a f6 c2 80 0f  |...p.s....s.....|
000000d0  84 f0 00 e9 83 00 66 0f  b6 c6 88 64 ff 40 66 89  |......f....d.@f.|
000000e0  44 04 0f b6 d1 c1 e2 02  88 e8 88 f4 40 89 44 08  |D...........@.D.|
000000f0  0f b6 c2 c0 e8 02 66 89  04 66 a1 48 7c 66 09 c0  |......f..f.H|f..|
00000100  75 4f 66 a1 44 7c 66 31  d2 66 f7 34 88 d1 31 d2  |uOf.D|f1.f.4..1.|
00000110  66 f7 74 04 3b 44 08 7d  38 fe c1 88 c5 30 c0 c1  |f.t.;D.}8....0..|
00000120  e8 02 08 c1 88 d0 5a 88  c6 bb 00 70 8e c3 31 db  |......Z....p..1.|
00000130  b8 01 02 cd 13 72 2a 8c  c3 8e 06 42 7c 60 1e b9  |.....r*....B|`..|
00000140  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 40  |....1.1.....a.&@|
00000150  7c be 77 7d e8 42 00 eb  0e be 7c 7d e8 3a 00 eb  ||.w}.B....|}.:..|
00000160  06 be 86 7d e8 32 00 be  8b 7d e8 2c 00 cd 18 eb  |...}.2...}.,....|
00000170  fe 00 00 00 00 00 00 47  65 6f 6d 00 48 61 72 64  |.......Geom.Hard|
00000180  20 44 69 73 6b 00 52 65  61 64 00 20 45 72 72 6f  | Disk.Read. Erro|
00000190  72 00 bb 01 00 b4 0e cd  10 ac 3c 00 75 f4 c3 00  |r.........<.u...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 24 12  |..............$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 c1 ff  eb 8d 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 b8 01 02 b5  00 b6 00 cd 13 72 d7 b6  |...p.........r..|
000001f0  01 b5 4f e9 e0 fe 00 00  00 00 00 00 00 00 55 aa  |..O...........U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by darkod on 2012-01-29
OK. I don't use wubi so I am not 100% sure, but I think you don't need the wubildr and wubildr.mbr files on /dev/sda3. But just in case you need them, don't delete them, just move them to another location. For example an external HDD.

Boot again in live mode, open /dev/sda3 and move wubildr and wubildr.mbr from it.

Restart and see if that helps boot vista.

---

### Post by Jonnyboy678 on 2012-01-29
how do i move the files??  Sorry for the stupid question, I was hoping to learn all about things when I had installed Ubuntu, but i'm having to learn a lot quicker than I thought just to try and get my laptop working again.

---

### Post by darkod on 2012-01-29
Same as in windows, you can use the Cut-Paste options. When you boot live mode, open your Home folder. That opens Nautilus, the file browser. On the left you will see a list of all partitions, click on the vista partition (if it has no name you can know which one is it by the size), that will mount it.
Look inside, select the both files and do a right-click Cut. After that just Paste to another location.

You can even move them to the same partition, in another folder. As long as they don't remain in the same place, in the root of the vista partition /dev/sda3.

---

### Post by drs305 on 2012-01-29
Do you still get the grub rescue prompt? If so, are you sure your system is not booting the sdb drive?

Sorry for jumping in. I'm gone again.... No need to respond.

---

### Post by Jonnyboy678 on 2012-01-29
> **darkod said:**
> Same as in windows, you can use the Cut-Paste options. When you boot live mode, open your Home folder. That opens Nautilus, the file browser. On the left you will see a list of all partitions, click on the vista partition (if it has no name you can know which one is it by the size), that will mount it.
Look inside, select the both files and do a right-click Cut. After that just Paste to another location.

You can even move them to the same partition, in another folder. As long as they don't remain in the same place, in the root of the vista partition /dev/sda3.

OK now i feel stupid, thought I had to do something via the terminal....

Copied the files out to a SD card to get them off the laptop but keeping them safe.  Did a reboot and straight back to the Grub Rescue Prompt again.  Ran the boot info script again as well and the results are below

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda6/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 479195136. According to the info 
                       in the boot sector, sda7 has 0 sectors.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 108288 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   136,710,143   105,046,016   7 NTFS / exFAT / HPFS
/dev/sda4         136,710,144   488,392,064   351,681,921   f W95 Extended (LBA)
/dev/sda5         136,712,192   347,453,819   210,741,628   7 NTFS / exFAT / HPFS
/dev/sda6         347,453,883   479,186,819   131,732,937   7 NTFS / exFAT / HPFS
/dev/sda7         479,195,136   488,392,064     9,196,929  49 Unknown


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        361C0AC01C0A7ADF                       ntfs       RECOVERY
/dev/sda2        0E220BBD220BA933                       ntfs       SYSTEM
/dev/sda3        A8DC0E05DC0DCF0E                       ntfs       
/dev/sda5        01CCDAC75E871580                       ntfs       
/dev/sda6        01CCDAC7622068E0                       ntfs       Ubuntu
/dev/sda7        4B13-E037                              vfat       
/dev/sdb1        54F2-021E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

============================= sda7/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# grub.cfg for a simple text menu.
# In the current architecture, this always just boots hyperspace.
# see normal/main.c
#
set quietmenu=1
set default=0
set timeout=0

menuentry "Hypercore" {
         sethsroot
         psaloader psa0
}
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1

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
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda6/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sda7

00000000  eb 4b 90 6d 6b 64 6f 73  66 73 00 00 02 04 3f 00  |.K.mkdosfs....?.|
00000010  02 00 02 00 10 f8 03 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 00 00 29 37  e0 13 4b 20 20 20 20 20  |......)7..K     |
00000030  20 20 20 20 20 20 46 41  54 31 32 20 20 20 04 00  |      FAT12   ..|
00000040  00 80 00 08 01 f0 8f 1c  00 00 00 00 80 fa eb 07  |................|
00000050  f6 c2 80 75 02 b2 80 ea  5c 7c 00 00 31 c0 8e d8  |...u....\|..1...|
00000060  8e d0 bc 00 20 fb a0 4c  7c 3c ff 74 02 88 c2 52  |.... ..L|<.t...R|
00000070  be 71 7d e8 23 01 be 05  7c f6 c2 80 74 48 b4 41  |.q}.#...|...tH.A|
00000080  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
00000090  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000a0  c7 04 10 00 66 8b 1e 44  7c 66 89 5c 08 66 8b 1e  |....f..D|f.\.f..|
000000b0  48 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |H|f.\..D..p.B..r|
000000c0  05 bb 00 70 eb 73 b4 08  cd 13 73 0a f6 c2 80 0f  |...p.s....s.....|
000000d0  84 f0 00 e9 83 00 66 0f  b6 c6 88 64 ff 40 66 89  |......f....d.@f.|
000000e0  44 04 0f b6 d1 c1 e2 02  88 e8 88 f4 40 89 44 08  |D...........@.D.|
000000f0  0f b6 c2 c0 e8 02 66 89  04 66 a1 48 7c 66 09 c0  |......f..f.H|f..|
00000100  75 4f 66 a1 44 7c 66 31  d2 66 f7 34 88 d1 31 d2  |uOf.D|f1.f.4..1.|
00000110  66 f7 74 04 3b 44 08 7d  38 fe c1 88 c5 30 c0 c1  |f.t.;D.}8....0..|
00000120  e8 02 08 c1 88 d0 5a 88  c6 bb 00 70 8e c3 31 db  |......Z....p..1.|
00000130  b8 01 02 cd 13 72 2a 8c  c3 8e 06 42 7c 60 1e b9  |.....r*....B|`..|
00000140  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 40  |....1.1.....a.&@|
00000150  7c be 77 7d e8 42 00 eb  0e be 7c 7d e8 3a 00 eb  ||.w}.B....|}.:..|
00000160  06 be 86 7d e8 32 00 be  8b 7d e8 2c 00 cd 18 eb  |...}.2...}.,....|
00000170  fe 00 00 00 00 00 00 47  65 6f 6d 00 48 61 72 64  |.......Geom.Hard|
00000180  20 44 69 73 6b 00 52 65  61 64 00 20 45 72 72 6f  | Disk.Read. Erro|
00000190  72 00 bb 01 00 b4 0e cd  10 ac 3c 00 75 f4 c3 00  |r.........<.u...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 24 12  |..............$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 c1 ff  eb 8d 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 b8 01 02 b5  00 b6 00 cd 13 72 d7 b6  |...p.........r..|
000001f0  01 b5 4f e9 e0 fe 00 00  00 00 00 00 00 00 55 aa  |..O...........U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by darkod on 2012-01-29
OK, few more files to move although I initially thought they should be no problem. They don't belong here anyway. Since we are running out of options lets clean up:
/dev/sda1 - move /boot/grub/core.img
/dev/sda6 - move /boot/grub/core.img

Restart and check if it changed anything.

If not, another thing might have relation but I can't explain it:
According to the script the starting sectors of sda5 and sda6 seem to be reported as 63 which is not true. Not sure if it can be related.

Try this above first, and lets see.

---

### Post by Jonnyboy678 on 2012-01-30
Darko, Many thanks for your continuing assistance with this. Bit of an update this morning.
 
Found and moved one of the core.img files but can't remember which one and couldn't find the second. However when I restarted it still got the grub rescue prompt. Restarted and set BIOS to load from hard drive rather than USB, same issue. Then tried to restart and enter the Samsung recovery app, and it wouldn't load and gave me an error about lack of wubildr files.
 
Did another restart and hit F10 and windows 7 unbelievably booted. So wondering what my options are now. Can I uninstall Ubunutu from add/remove programs, don't want to do this yet incase it causes me more issues? If i did uninstall it, I would then re-install from the USB drive rather than using WUBI.
 
Edit - And one other thing, when I re-ran the boot info script this morning, all my drives which were previously /dev/sda1/, /dev/sda2/ etc are now /dev/sdb1/, dev/sdb2/.  No idea why that changed.

---

### Post by Jonnyboy678 on 2012-01-30
Just wanted to update thread again.  After re-booting netbook again, I now get the windows bootloader and can select either windows 7 or Ubuntu.  Windows 7 works fine, but Ubuntu doesn't load.  

I'm thinking I should uninstall ubuntu from add/remove programs in windows, and then re-install via the USB drive.??  Would this be the best course of action.

Thanks again Darko for all your help.

---

### Post by darkod on 2012-01-30
Actually, when we started moving files. those first two files, wubildr and wubildr.mbr from /dev/sda3 might have been in the correct place. As I said I'm not 100% sure where wubi keeps all files.
If you have them around, you can try putting them back.

Another approach is removing wubi from Add/Remove and later plan a proper dual boot install.

At this point it's up to you. At least we got windows booting. :)

---

