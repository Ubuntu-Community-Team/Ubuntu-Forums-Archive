---
title: "Lost Windows 7 boot option in grub"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by scooter217 on 2011-01-12
I had a working dual boot Ubuntu 10 and Windows 7.   Anyways long story short, I got it working again but have lost the boot option for windows 7.  If i run fdisk -l, I get the following.

root@support-Latitude-E6400:/home/support# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079723

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4871    39118848   83  Linux
/dev/sda2            4871       15326    83983361    5  Extended
/dev/sda3   *       15327       30401   121089937+   7  HPFS/NTFS
/dev/sda5            4871        5479     4881408   82  Linux swap / Solaris
/dev/sda6            5479       15326    79100928    7  HPFS/NTFS

I installed gparted and can see that windows 7 is installed in dev/sda6.  In another forum, i read that someone had to edit their menu.lst so i did with the following.  

title=Windows 7
rootnoverify (hd0,6)
makeactive
chainloader +1

When i try to boot from windows 7, i get the following error. Error 12: invalid device request.  How can i get my laptop to boot from windows again?

---

### Post by Quackers on 2011-01-12
Welcome to UF.
You say you got it working again, but you don't say what was wrong. Which version of Ubuntu are you using (you say 10)? If you are using 10.04 or 10.10 which both use grub2, the menu.lst should be empty (as grub2 doesn't use that file).

Which operating system was installed first?

It may be an idea to go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by scooter217 on 2011-01-12
I wasnt able to boot to Ubuntu or Windows 7 at first.  But i found a post that suggested to use Super Grub to detect the os and log into ubuntu.  Then i installed grub (apt-get install grub) and ran the following.

```

sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```
then I updated grub. This generated the menu.lst and then enabled me to select ubuntu to boot.  But now Windows 7 is not an option to boot from.  its gone.
  ( When you first turn on your pc, you get a boot option to boot to Ubuntu or Windows). I had been trying to get this to work for the past 3 days.  I am running Ubuntu 10.10.  Ubuntu was the first os installed.  Below is the results.txt file you requested.

```


 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    78,239,743    78,237,696  83 Linux
/dev/sda2          78,241,790   246,208,511   167,966,722   5 Extended
/dev/sda5          78,241,792    88,004,607     9,762,816  82 Linux swap / Solaris
/dev/sda6          88,006,656   246,208,511   158,201,856   7 HPFS/NTFS
/dev/sda3    *    246,212,190   488,392,064   242,179,875   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        dc7cacd2-0e33-48ea-a05c-5692273d462c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        52FCAB8B6DCE4233                       ntfs       backup                        
/dev/sda5        8f39510c-53b7-47db-b8e6-a30430160173   swap                                     
/dev/sda6        7CAE79F0AE79A2F6                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dc7cacd2-0e33-48ea-a05c-5692273d462c

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

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		dc7cacd2-0e33-48ea-a05c-5692273d462c
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		dc7cacd2-0e33-48ea-a05c-5692273d462c
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		dc7cacd2-0e33-48ea-a05c-5692273d462c
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		dc7cacd2-0e33-48ea-a05c-5692273d462c
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		dc7cacd2-0e33-48ea-a05c-5692273d462c
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		dc7cacd2-0e33-48ea-a05c-5692273d462c
kernel		/boot/memtest86+.bin
quiet

title=Windows 7
rootnoverify (hd0,6)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dc7cacd2-0e33-48ea-a05c-5692273d462c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 52fcab8b6dce4233
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=dc7cacd2-0e33-48ea-a05c-5692273d462c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8f39510c-53b7-47db-b8e6-a30430160173 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.6GB: boot/grub/core.img
  30.5GB: boot/grub/grub.cfg
  24.8GB: boot/grub/menu.lst
   6.6GB: boot/grub/stage2
   1.6GB: boot/initrd.img-2.6.35-22-generic
   1.6GB: boot/initrd.img-2.6.35-24-generic
   6.7GB: boot/vmlinuz-2.6.35-22-generic
   6.7GB: boot/vmlinuz-2.6.35-24-generic
   1.6GB: initrd.img
   1.6GB: initrd.img.old
   6.7GB: vmlinuz
   6.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ee ea 5a 6a d3 9f cc f4  ea b7 b2 62 af 9b 51 8f  |..Zj.......b..Q.|
00000010  d5 96 cb 6e fd bb 62 9b  35 3b 66 95 b3 c3 d0 d3  |...n..b.5;f.....|
00000020  df 48 96 16 20 05 46 4f  00 47 60 d3 8d 87 2d 3b  |.H.. .FO.G`...-;|
00000030  d2 98 f5 89 7b 26 b5 0b  d5 5a 99 fb 8b 1a 7e a8  |....{&...Z....~.|
00000040  96 d5 47 2f 25 34 0b c2  d3 13 58 c8 c1 9e 78 ae  |..G/%4....X...x.|
00000050  52 f8 6d a2 ae 24 39 98  6b 12 3d ab 2d 6b 5a eb  |R.m..$9.k.=.-kZ.|
00000060  e7 16 ff b8 7f a8 e4 48  68 86 28 30 d8 0a 16 20  |.......Hh.(0... |
00000070  0b 9c d4 fd ef 56 b1 f1  77 2e 8b ad f7 1e f5 7f  |.....V..w.......|
00000080  10 91 55 f1 6c ee c8 f9  7c fd 5a 3b 0f 16 20 75  |..U.l...|.Z;.. u|
00000090  b3 35 f3 cc eb 55 55 58  d5 10 4d 86 8f f7 ff f2  |.5...UUX..M.....|
000000a0  34 a7 1c 6a b9 43 18 10  88 01 78 2f a8 ce a3 4a  |4..j.C....x/...J|
000000b0  1e 51 0b 7e 22 91 58 32  34 eb 4e 48 ff fb b2 00  |.Q.~".X24.NH....|
000000c0  ea 0e e4 da 63 51 0b 58  43 72 9e 6c 7a 21 69 eb  |....cQ.XCr.lz!i.|
000000d0  6e 10 8d 61 48 4d 3d 0d  ca 3b 2b e8 c5 a7 a1 ba  |n..aHM=..;+.....|
000000e0  9b aa 88 5b 8b 0e 2a bd  bc dd 7a ac 88 4d 49 b2  |...[..*...z..MI.|
000000f0  f3 34 7a b0 36 8b a6 ca  93 15 76 8f cb 6a b1 1f  |.4z.6.....v..j..|
00000100  16 1d 14 b8 99 fd b5 2b  9b c8 52 da fb dd 75 7d  |.......+..R...u}|
00000110  e0 bb ba 6e 84 01 50 ec  c4 15 40 a8 86 1c 1e 23  |...n..P...@....#|
00000120  35 4c 2e fd ec d7 c7 2f  73 52 d7 a7 57 56 bc 42  |5L...../sR..WV.B|
00000130  47 5d 43 b3 bb 23 e5 c4  c7 36 8e c3 c3 e2 07 59  |G]C..#...6.....Y|
00000140  d6 cd cf 3f 35 4a b5 44  a9 2a 91 19 f4 a5 95 8a  |...?5J.D.*......|
00000150  01 8b 22 f0 a5 7f fe d4  2d 00 00 73 03 0f 31 01  |..".....-..s..1.|
00000160  91 f1 c0 0a c1 de 87 a6  b2 c4 74 99 73 76 a6 80  |..........t.sv..|
00000170  9a 64 a9 f8 95 d6 ab 08  87 24 d1 aa 2d ca ad b7  |.d.......$..-...|
00000180  26 94 39 e9 0c c5 98 0e  22 9c f2 44 e2 7b 55 4e  |&.9....."..D.{UN|
00000190  8a 0b 85 54 81 b0 81 ad  5a a6 b5 af fb db ed 4d  |...T....Z......M|
000001a0  e7 8e 38 ef 5f fd 8e f9  96 5b ac 94 f1 4c e9 e9  |..8._....[...L..|
000001b0  3c 6a 37 96 8f 6e 34 3a  ad 7b dd bb ae a6 00 fe  |<j7..n4:.{......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 94 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f8  94 00 00 00 6e 09 00 00  |............n...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Quackers on 2011-01-12
How are you using grub legacy instead of grub2, which is the default for Ubuntu 10.10?

---

### Post by scooter217 on 2011-01-12
I was able to install it through the supergrub.iso disk.  I wonder if reinstalling grub2 would fix the problem.

---

### Post by kansasnoob on 2011-01-12
Having mixed grub2 and legacy grub files tends to mess things up. Can you boot into your installed Ubuntu?

---

### Post by oldfred on 2011-01-12
Since you are booting from sda3, it windows may work as it has to boot from a primary NTFS partition with the boot flag. But your main install was copied.

> sda6: _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at [COLOR=Red]sector 2048[/COLOR].


Windows will not work with that inconsistency. I do not know if windows will repair that since it is a logical partition. Testdisk does have a rebuild NTFS boot sector function that may work.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by yahmon on 2011-01-12
Maybe somebody can do a sticky on grub2?
I got confused with all the different grub how to's on the net.
If grub2 is present all you have to type is "sudo update-grub" in the terminal and it will find your windows or other operating system, then grub.d will write it to grub.cfg file
Reboot and voila

---

### Post by hansolo4949 on 2011-01-12
"Ubuntu was the first os installed"


I would love to know how you got that to work, because Windows usually overwrites grub and replaces it with it's own bootloader. maybe that's you problem?

hansolo4949

---

### Post by scooter217 on 2011-01-12
Anything is possible, just harder sometimes.  I am going to mess around with a few things and then will reply to this post in the morning.  if i cant figure it out tonight, i am just going to rebuild the laptop.  Next time i will make an image of it with Clonezilla before i break it!!!.

---

### Post by kansasnoob on 2011-01-12
> **scooter217 said:**
> Anything is possible, just harder sometimes.  **[COLOR="Red"]I am going to mess around with a few things[/COLOR]** and then will reply to this post in the morning.  if i cant figure it out tonight, i am just going to rebuild the laptop.  Next time i will make an image of it with Clonezilla before i break it!!!.

You've already done too much "messing around"!

You need to pay attention and answer questions when they're asked, like:

> Can you boot into your installed Ubuntu? 

The first thing to do is properly straighten out grub2! Then if Windows fails to boot it's time to try booting Windows using a Windows readable MBR. And you need to know how to properly recover a grub2 MBR.

But, if you like chasing your own tail that's fine :(

We also need to know for sure if you have an Ubuntu Live CD that you can run and what version it is.

---

### Post by scooter217 on 2011-01-13
Thanks for all the suggestions.  I decided to wipe the laptop.  @kansasnoob - "messing around" with Ubuntu is what makes us more experienced and we learn from our mistakes".

---

### Post by hansolo4949 on 2011-01-13
I agree, scooter. I have had to reinstall Ubuntu multiple times on one of the computers I have it on because I liked to "mess around" with it. I think that's just about the fastest way you can learn. Get your hands dirty:).

I hope to reinstallation works well!

hansolo4949

---

### Post by weedeater64 on 2011-01-13
> **Quackers said:**
> How are you using grub legacy instead of grub2, which is the default for Ubuntu 10.10?


That's what I want to know, that's why I'm here today to find out how to accomplish that....

I have a Debian box with space for two more partitions for other distro's and I want to install the new Ubuntu to one of them...

[U][I][B]I do not want Ubuntu to take control of booting, install a boot loader, change my grub, or any of that.... 
[/B][/I][/U]

I know how to make an entry in menu.lst  of grub, and would prefer to do so myself.

Anyone???

IMO the install process of Ubuntu is a bit too much like winbloze.

---

### Post by weedeater64 on 2011-01-13
> **kansasnoob said:**
> Having mixed grub2 and legacy grub files tends to mess things up. Can you boot into your installed Ubuntu?

I can vouch for that, I'm still in the process of cleaning up the mess that resulted from allowing grub2 on my box.:mad:

---

