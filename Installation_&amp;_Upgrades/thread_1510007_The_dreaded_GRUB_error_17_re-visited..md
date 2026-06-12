---
title: "The dreaded GRUB error 17 re-visited."
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by netbook on 2010-06-15
Gentlemen, 

I have a serious problem. I have been dual booting with windows xp on my laptop for some time now. I decided that I wanted to make the switch to ubuntu full force and downloaded a live version of xubuntu to do a little partition editing. I shrunk my windows to the minimum amount I could while retaining necessary programs. Then deleted an unused logical partition within the extended partition where Ubuntu and my linux swap partition was located. The changes were applied (after 2 hours copying files) and I re-booted. 
Surprise surprise GRUB error 17, I now realize GRUB is likely looking for the now incorrectly named partition. 
After some research this morning I have tried several solutions but am having no luck. Here is the result of running sudo fdisk -l

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

suubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2107a38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        2697    15360000+   7  HPFS/NTFS
/dev/sda3            2698       19457   134624700    5  Extended
/dev/sda5            2698       19188   132463926   83  Linux
/dev/sda6           19189       19457     2160711   82  Linux swap / Solaris

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         983     7895916    b  W95 FAT32

any help greatly appreciated. 

Netbook

---

### Post by netbook on 2010-06-15
Additional hopefully useful info. On 9.04 version of Ubuntu. 

Thanks

---

### Post by netbook on 2010-06-16
Any help anyone?

---

### Post by confused57 on 2010-06-16
It might help someone see your problem if you can post the results of the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by netbook on 2010-06-17
Fixed

---

### Post by Dn4mycrownj on 2010-06-17
```
> **netbook said:**
> Here is the boot info requested above, I know it's alot but that is the entire contents of the resulting text file. Hopefully someone can help me out now. 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960    43,314,960    30,720,001   7 HPFS/NTFS
/dev/sda3          43,327,305   312,576,704   269,249,400   5 Extended
/dev/sda5          43,327,368   308,255,219   264,927,852  83 Linux
/dev/sda6         308,255,283   312,576,704     4,321,422  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,791,894    15,791,832   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AE982D64982D2BF1                       ntfs       PQSERVICE                     
/dev/sda2        0604F73B04F72BF5                       ntfs       ACER                          
/dev/sda3: PTTYPE=&quot;dos&quot; 
/dev/sda5        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4   ext3                                     
/dev/sda6        b48f0565-cb14-42cc-a0fe-c2e69ae93995   swap                                     
/dev/sda: PTTYPE=&quot;dos&quot; 
/dev/sdb1        1F65-ECCC                              vfat                                     
/dev/sdb: PTTYPE=&quot;dos&quot; 

============================ &quot;mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS=&quot;Microsoft Windows XP Home Edition&quot; /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d86ca883-1e0e-4de6-ac7b-0b00ae9d5dd4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=a0b68088-949e-451f-a4b9-2849d3beac78 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  22.7GB: boot/grub/menu.lst
  22.6GB: boot/grub/stage2
  23.5GB: boot/initrd.img-2.6.28-11-generic
  22.7GB: boot/initrd.img-2.6.28-13-generic
  22.7GB: boot/initrd.img-2.6.28-15-generic
  24.2GB: boot/vmlinuz-2.6.28-11-generic
  23.8GB: boot/vmlinuz-2.6.28-13-generic
  22.9GB: boot/vmlinuz-2.6.28-15-generic
  22.7GB: initrd.img
  22.7GB: initrd.img.old
  22.9GB: vmlinuz
  23.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  aa 5f 05 cd 49 79 9f 13  17 b0 d5 17 70 0b df f6  |._..Iy......p...|
00000010  72 31 2d f5 fc 10 71 aa  78 01 e7 0a 84 b7 2e 6d  |r1-...q.x......m|
00000020  6e 1c 61 f8 5a b0 39 a0  68 c9 5c cb 96 10 e2 ce  |n.a.Z.9.h.\.....|
00000030  f9 1d a6 7c 51 f8 2e 8b  70 41 2a f4 d9 b5 23 65  |...|Q...pA*...#e|
00000040  82 32 fe 54 9e 9b b3 c6  6c 19 5c 07 2f ef f5 bb  |.2.T....l.\./...|
00000050  e3 43 c5 6f d1 3d d5 76  8c 3b a3 f1 e9 3c d3 b2  |.C.o.=.v.;...<..|
00000060  fc dc 7b cc c0 74 2d 66  eb a5 d3 df 9b 98 11 be  |..{..t-f........|
00000070  bb ed 0c 1d ce 7f 1a bd  27 ea 31 f1 bc 0c fd 7d  |........'.1....}|
00000080  fc 32 a6 20 30 fb 38 d8  f7 02 5b 37 9d 82 9a cf  |.2. 0.8...[7....|
00000090  82 e3 a9 23 1f 16 42 d8  c3 88 f3 e7 69 4a bd 8a  |...#..B.....iJ..|
000000a0  f5 f4 d2 f9 d3 2e 67 46  ad 3e fe e8 73 07 cb c8  |......gF.>..s...|
000000b0  6f db e2 0d e7 4c de 35  73 8c ce 32 af d5 42 fc  |o....L.5s..2..B.|
000000c0  65 db de 67 ab f6 7f ac  9a 9e 70 7b aa d1 25 41  |e..g......p{..%A|
000000d0  e1 28 1b d6 cc aa 5e b7  7b 06 ca 6a 47 4e 08 7c  |.(....^.{..jGN.||
000000e0  72 4a bb 9a 18 d2 5f 77  8a a9 bc e1 a8 ca 94 f2  |rJ...._w........|
000000f0  fd c9 46 9d 2c e4 e2 11  25 5f 21 6c 3a 34 ea d8  |..F.,...%_!l:4..|
00000100  08 de d7 d5 6f 07 25 3f  bd 15 9a b8 77 8e a1 81  |....o.%?....w...|
00000110  f1 32 69 d3 86 16 3d 2f  c7 08 79 7f c8 eb 99 30  |.2i...=/..y....0|
00000120  69 60 d6 e4 f3 e8 e3 43  63 c3 79 e6 e3 9f 0a 87  |i`.....Cc.y.....|
00000130  ab 31 4d 45 22 d5 14 36  a7 70 ef 04 47 83 27 19  |.1ME&quot;..6.p..G.'.|
00000140  e9 fa 6b ca 33 d4 1c 73  63 08 5b 5e fc 89 4d 53  |..k.3..sc.[^..MS|
00000150  8c 9f a2 8d c9 42 0f dd  db 61 bb 7f 8d 24 86 d5  |.....B...a...$..|
00000160  bf f9 35 1c 70 fa 63 60  b0 68 e3 88 0e 97 73 3b  |..5.p.c`.h....s;|
00000170  a3 54 e6 9c 14 a7 e4 df  9e 63 f3 c1 81 08 12 0f  |.T.......c......|
00000180  4c 6e e1 97 5c f8 5d b8  e1 e5 98 37 5c 61 c8 83  |Ln..\.]....7\a..|
00000190  b6 01 2a cb 9d b2 c3 96  5b e8 b6 f9 ec 09 2d 3a  |..*.....[.....-:|
000001a0  b4 56 b4 d5 c6 3a 39 72  fc 7c da 83 21 c7 f7 9f  |.V...:9r.|..!...|
000001b0  9d 7c 6c 2b 51 70 5a 5f  7c 65 c5 93 d1 99 00 fe  |.|l+QpZ_|e......|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 6c 7a ca 0f 00 fe  |......?...lz....|
000001d0  ff ff 05 fe ff ff ab 7a  ca 0f cd f0 41 00 00 00  |.......z....A...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```  repost from above me to make it readable

---

### Post by netbook on 2010-06-17
Hey thanks man.

---

### Post by confused57 on 2010-06-17
You might want to check this explanation & possible solutions for grub error 17:
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

Your UUID appears to be correct in your menu.lst for your root partition, which means you may need to do a file system check, according to the recommendations in Herman's link.

---

### Post by netbook on 2010-06-17
Thanks again for the speedy responses. I read the information on Herman's blog and found it very useful however the only suggestion he has for 9.04 + is to do a file system check to resolve GRUB errors. I did so off my live xubuntu boot using g-parted as he mentions however I still suffer from the same error. Any other suggestions, this is quite frustrating to me. Thanks for all the help so far.

---

### Post by confused57 on 2010-06-17
Try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

There should be someone else who might see something in the results from your bootinfo script and can help you.

---

### Post by confused57 on 2010-06-17
If reinstalling grub doesn't work & you have access to another computer, download & burn a copy of Super Grub Disk:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

See if SGD can boot Ubuntu or Windows or if it gives you a different grub error.  SGD can also be used to repair the mbr for either Windows or Linux.

---

### Post by netbook on 2010-06-17
So I am definitely an ubuntu noob so can someone help me out here. I am trying to just do the re-install as mentioned in the above post but running "sudo grub" (without " " obviously) in the terminal returns the following. 

sudo: grub: command not found

I am running on a xububntu live usb so I assume it is because it is looking on the usb not on the hard drive, any idea on how to fix this?

Or any other input would be appreciated. 

Netbook

^
Also I have a netbook so while I do have access to another computer that will not be terribly useful due to my lack of an optical drive. Thanks for the idea though and my apologies for being too vague.

---

### Post by confused57 on 2010-06-17
You would need a live usb of Ubuntu 9.04 or an earlier version to reinstall grub to the mbr, I'm assuming your Xubuntu is 10.04.

If you need to be able to boot into Windows for now, you might want to check out these instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

You'll mainly just need to run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore any warnings it might give you when running the commands.

It's getting late here, so I'll have to call it a night; but there should be plenty other experienced people here who can help you.

---

### Post by netbook on 2010-06-17
New idea. Is there anyway to access my data (files etc) from my live boot. I could just copy everything I want to an external drive and then do a clean install of 10.04 by re-formatting my and and starting all over. So is it possible to get at that stuff via my live boot?

---

### Post by wilee-nilee on 2010-06-17
> **netbook said:**
> New idea. Is there anyway to access my data (files etc) from my live boot. I could just copy everything I want to an external drive and then do a clean install of 10.04 by re-formatting my and and starting all over. So is it possible to get at that stuff via my live boot?

Yes just go to the places computer and click on the hd or home I'm not sure which, I have never had to recover stuff

The script shows that it is looking for the grub files in sda6 which is a swap partition. It looks like everything is in the right place but grub.97 is just not looking in the correct place.

Personally I think this is fixable I just am not familiar with legacy grub but others are and are on line during the early morning to about 9 pm US west coast time. If you can hang for their help you might be able to get this fixed. 

If you have run any fixes since posting the script originally run it again and post it and hang for help.

If you can delete the first script post so the thread page is not so long that would be helpful, just put a letter in place of the script. Leave the script in code tags there but delete the one above it.;)

---

### Post by confused57 on 2010-06-17
> **netbook said:**
> New idea. Is there anyway to access my data (files etc) from my live boot. I could just copy everything I want to an external drive and then do a clean install of 10.04 by re-formatting my and and starting all over. So is it possible to get at that stuff via my live boot?

You shouldn't have any problems accessing your data on your root partition, first you'll need to mount it by opening a terminal:
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```

Then you should be able to open  "file system", open the "media" directory, and open your sda5 partition.  Plug in your external drive, then backup your data.

---

### Post by Dn4mycrownj on 2010-06-17
Did you choose to encrypt the files when you installed, if so that is going to make it a litte hard to view and recovery them. That is just speaking from experience. I used bt4 because it is on my other partition, but Knoppix is a live OS that can change the read and write permissions on a mounted hard drive. That could be a little help. I do not know how to do it from Knoppix, but I do know that you can mount a partition and then open up a root terminal in that partition. At that point you can read and write things to the partition when it is not accessible any other way.

---

### Post by Dn4mycrownj on 2010-06-17
I dont know alot about this but, in his info it says the boot start at sector 63, does grub look for it at sector 0.   I am just asking I am not sure of any of this. 

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,791,894    15,791,832   b W95 FAT32




 default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0



That are the two things I am looking at. Can someone follow up and tell me if I am going  in the right direction or not.

---

