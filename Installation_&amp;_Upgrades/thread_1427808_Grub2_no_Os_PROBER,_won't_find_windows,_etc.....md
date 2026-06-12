---
title: "Grub2 no Os_PROBER, won't find windows, etc...."
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by MechanicalDaddy on 2010-03-12
Hello all,
I am trying to dual-boot windows xp and ubuntu 8.04LTS from two separate hard drives, on a compaq d510 evo SFF.   With research, the best way to do that seemed to be to upgrade to Grub 2 and all would be well...not so much.

I installed each OS with the other hard drive removed, fyi.

I believe that this tells me that I SHOULD be able to boot off either drive, if I could get Grub 2 to recognize...

```
steve@Stewie:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb788b788

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4785    38435481   83  Linux
/dev/sda2            4786        4870      682762+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0abe10f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5168    39070048+   7  HPFS/NTFS


```But it appears that the 30_OS-Prober and 40_-custom are either hidden or disabled...and no matter how many times I "sudo update-grub" the windows entry will not get added :mad:  

note here: on my screen all the files in grub.d folder are green except for 30 and 40
```
steve@Stewie:~$ ls /etc/grub.d
00_header        10_hurd   20_memtest86+  40_custom~
05_debian_theme  10_linux  30_os-prober~  README
``````
steve@Stewie:~$ sudo update-grub
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.24-27-generic
Found initrd image: /boot/initrd.img-2.6.24-27-generic
Found linux image: /boot/vmlinuz-2.6.24-26-generic
Found initrd image: /boot/initrd.img-2.6.24-26-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```I have also tried adding the proper code to the 40 custom file, and while I could at least get it to acknowledge my changes, I couldn't seem to find the magic code to get it right....

The other thing I tried was adding GRUB_DISABLE_OS_PROBER=false
to /etc/default/grub

and last but not least, here is my results.txt from the boot info script.

Any and all help is GREATLY appreciated!  

PS:  looking at the results...I also tried uninstalling/reinstalling grub 2, perhaps I created issues there?

Steve in Maine

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb788b788

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    76,871,024    76,870,962  83 Linux
/dev/sda2          76,871,025    78,236,549     1,365,525  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0abe10f2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1   ext3                                     
/dev/sda2        87af847d-cdf6-47b5-86dd-fa2df3ed59ee   swap                                     
/dev/sdb1        8EC42C05C42BEE61                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro single
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro single
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault

title        Debian GNU/Linux, kernel memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=20
set root=(hd0,1)
if font (hd0,1)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.24-27-generic" {
    linux    (hd0,1)/boot/vmlinuz-2.6.24-27-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro quiet splash
    initrd    (hd0,1)/boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu, linux 2.6.24-27-generic (single-user mode)" {
    linux    (hd0,1)/boot/vmlinuz-2.6.24-27-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro single
    initrd    (hd0,1)/boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu, linux 2.6.24-26-generic" {
    linux    (hd0,1)/boot/vmlinuz-2.6.24-26-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro quiet splash
    initrd    (hd0,1)/boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu, linux 2.6.24-26-generic (single-user mode)" {
    linux    (hd0,1)/boot/vmlinuz-2.6.24-26-generic root=UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 ro single
    initrd    (hd0,1)/boot/initrd.img-2.6.24-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd0,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=87c9cf0d-1e07-4549-b7cc-b12f7d5f89b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=87af847d-cdf6-47b5-86dd-fa2df3ed59ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
    .3GB: boot/grub/grub.cfg
    .3GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.24-26-generic
    .3GB: boot/initrd.img-2.6.24-27-generic
    .2GB: boot/initrd.img-2.6.24-27-generic.bak
    .3GB: boot/vmlinuz-2.6.24-26-generic
    .3GB: boot/vmlinuz-2.6.24-27-generic
    .3GB: initrd.img
    .3GB: initrd.img.old
    .3GB: vmlinuz
    .3GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 4b 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.K....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 04 00  |...It.8,t.......|
00000040  00 80 00 08 01 00 00 00  00 00 00 00 ff fa 90 90  |................|
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
00000170  fe 47 52 55 42 20 00 47  65 6f 6d 00 48 61 72 64  |.GRUB .Geom.Hard|
00000180  20 44 69 73 6b 00 52 65  61 64 00 20 45 72 72 6f  | Disk.Read. Erro|
00000190  72 00 bb 01 00 b4 0e cd  10 ac 3c 00 75 f4 c3 00  |r.........<.u...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  88 b7 88 b7 00 00 80 01  |................|
000001c0  01 00 83 fe ff ff 3f 00  00 00 32 f5 94 04 00 fe  |......?...2.....|
000001d0  ff ff 82 fe ff ff 71 f5  94 04 15 d6 14 00 00 00  |......q.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by mikewhatever on 2010-03-12
What made you think you needed Grub2 to boot the two OSs? Obviously, you could have done just fine with the default boot loader. Apparently, Grub2 is available in Hardy's repositories, but the version is 1.96, as opposed to 1.97, which is beta4 in Karmic. It may have been added for testing purposes, who knows.

---

### Post by MechanicalDaddy on 2010-03-12
Well Mikewhatever,
I was trying to keep the installations as separate as possible, as I got tired of re-installing Ubuntu when XP SP3 would cause a major boot failure (I know, I probably shouldn't have had to, but nothing I tried as far as re-installing grub was working out so well).   The lure of "just run update-grub and it will find your windows installation" was too great, and being pretty new at this, it seemed like a good choice.  Do you have any actual suggestions with either boot loader?
Thanks,
Steve

---

### Post by mikewhatever on 2010-03-12
Suggestions, I don't know. You seem to have both /boot/grub/menu.lst for grub1 and /boot/grub/grub.cfg for grub2. Do you know if grub1 got uninstalled when you ungraded? I guess my suggestion is, unless someone else has better ideas, revert to the original boot loader, since grub2 may not be fully functional in Hardy.

---

### Post by stlsaint on 2010-03-12
U need to remove grub from your system and ensure that grub2 is on the master hdd mbr

---

### Post by MechanicalDaddy on 2010-03-12
Before I read the last two posts, I tried to remove Grub legacy, and yeah, there was definitely remnants of both.  Even though it said I was successful at removing grub legacy, when I rebooted, it still said version 1.96.  
In order to fix the dual grub issue, I decided just to go with re-installing Ubuntu again, this time with both hard drives on, and surprise surprise, everything works as I want it to.  I believe that with the two hard drives, that if XP explodes again, Ubuntu should remain functional.  

If anyone else is having an issue, here is the menu.lst option that was added (and I searched all over for) that adds my XP installation  

```
 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

Thank you folks for your help, I appreciate it!

---

