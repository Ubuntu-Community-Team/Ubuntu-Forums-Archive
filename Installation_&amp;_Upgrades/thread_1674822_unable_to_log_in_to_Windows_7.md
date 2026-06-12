---
title: "unable to log in to Windows 7"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by mac4rfree on 2011-01-24
Hi guys,

I was able to log in to Windows 7 till yesterday.. Don know what happened now i am not able to login to windows 7 itself.. It directly login to Ubuntu..

Below is my Boot script output
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 172241936 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sda2         327,708,670   625,121,279   297,412,610   f W95 Ext d (LBA)
/dev/sda5         331,613,793   625,121,279   293,507,487   7 HPFS/NTFS
/dev/sda6         327,708,672   331,612,159     3,903,488  82 Linux swap / Solaris
/dev/sda3         167,768,064   327,706,623   159,938,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B01E99FA1E99BA34                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        e63d174c-5dab-4cd7-8729-57820a142ea8   ext4                                     
/dev/sda5        0E302F6A302F57CB                       ntfs                                     
/dev/sda6        53fc5384-e24b-455f-8f4f-a16f5a74bc7a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/0E302F6A302F57CB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e63d174c-5dab-4cd7-8729-57820a142ea8

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
uuid		e63d174c-5dab-4cd7-8729-57820a142ea8
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		e63d174c-5dab-4cd7-8729-57820a142ea8
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		e63d174c-5dab-4cd7-8729-57820a142ea8
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		e63d174c-5dab-4cd7-8729-57820a142ea8
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		e63d174c-5dab-4cd7-8729-57820a142ea8
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		e63d174c-5dab-4cd7-8729-57820a142ea8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e63d174c-5dab-4cd7-8729-57820a142ea8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b01e99fa1e99ba34
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e63d174c-5dab-4cd7-8729-57820a142ea8 /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  88.1GB: boot/grub/core.img
  94.9GB: boot/grub/grub.cfg
  88.1GB: boot/grub/menu.lst
  88.1GB: boot/grub/stage2
  86.9GB: boot/initrd.img-2.6.35-22-generic
  89.2GB: boot/initrd.img-2.6.35-24-generic
  88.1GB: boot/vmlinuz-2.6.35-22-generic
  88.1GB: boot/vmlinuz-2.6.35-24-generic
  89.2GB: initrd.img
  86.9GB: initrd.img.old
  88.1GB: vmlinuz
  88.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  97 f5 7e ee a5 b5 82 ea  b7 34 88 3b 37 02 35 89  |..~......4.;7.5.|
00000010  9e 0c f2 b1 be b2 75 36  65 75 5c cc 7c e7 3d cc  |......u6eu\.|.=.|
00000020  a1 8d fb 36 30 9d b7 dc  f0 36 ee 0d e7 53 f7 7c  |...60....6...S.||
00000030  c2 a9 d2 37 63 7d 5f eb  38 36 88 b2 97 fb 87 c4  |...7c}_.86......|
00000040  b5 ba 7c d8 92 9d 4e a5  fe 32 ac c0 c7 c4 2d a5  |..|...N..2....-.|
00000050  8f ba ca db 65 a2 4e c6  07 6a 00 ef 24 78 9d 3c  |....e.N..j..$x.<|
00000060  d6 bf d6 2f ac f9 18 8f  c3 c5 e9 f5 b5 f7 e5 0d  |.../............|
00000070  cd 0f fa 2d 64 4c 98 23  9f 8a e2 07 49 f4 7e ab  |...-dL.#....I.~.|
00000080  3b 2d c3 73 ee bd 90 79  21 95 93 5b 7f 19 f9 2d  |;-.s...y!..[...-|
00000090  ae a7 73 3a 67 54 e8 bd  46 f9 6d 03 19 ac 73 a0  |..s:gT..F.m...s.|
000000a0  9d ae 0d 77 22 24 7d 34  94 dc ff 00 16 f9 2e cc  |...w"$}4........|
000000b0  bf aa dc f6 6c 73 ee 6b  8b 7f 74 9d e4 8f 91 4d  |....ls.k..t....M|
000000c0  fe 30 f3 69 c4 cd e9 2f  b5 d0 2b b8 d8 ee 49 0c  |.0.i.../..+...I.|
000000d0  06 bd 60 7c 13 7f 8b 4b  c6 45 dd 51 f1 b4 be e6  |..`|...K.E.Q....|
000000e0  bf 69 d0 8d c6 c3 a8 47  fa ff 00 55 76 65 f4 71  |.i.....G...Uve.q|
000000f0  63 5a e0 72 76 90 e0 08  2d 25 93 20 f2 92 9c de  |cZ.rv...-%. ....|
00000100  87 d7 b1 7a 8f d6 bb 32  2a 71 2c ba 9f 4d 84 82  |...z...2*q,..M..|
00000110  25 cd 0d 3f 8e d3 ca 07  d6 5c ec be ad d7 30 45  |%..?.....\....0E|
00000120  38 ae a2 c6 12 da 8e 40  80 f7 03 3b 88 6c e8 de  |8......@...;.l..|
00000130  44 13 2b 4f a7 b2 ba 3e  b7 dc d6 57 b1 bf 67 da  |D.+O...>...W..g.|
00000140  d0 1b b5 b2 03 0f b4 01  0a 7f 5b 2c 6d 3f 58 7a  |..........[,m?Xz|
00000150  3b 9e 40 12 44 9f 12 60  7e 29 29 6f ad dd 43 3b  |;.@.D..`~))o..C;|
00000160  17 a3 1c 4c ac 77 5d 6b  eb 1e a5 d5 80 31 d9 0e  |...L.w]k.....1..|
00000170  91 e7 3a 0d 36 81 3c 15  1f ab f6 75 6e 9b d0 ec  |..:.6.<....un...|
00000180  c8 73 e9 15 37 13 d4 a0  34 12 e6 96 82 e9 70 20  |.s..7...4.....p |
00000190  0d 7b ea 75 5b 9f 5e 7f  e4 4c cf ea 0f fa a0 a8  |.{.u[.^..L......|
000001a0  63 5a db 7e a9 4b 1d 20  61 39 ba 78 b5 a5 ae 1f  |cZ.~.K. a9.x....|
000001b0  22 92 9c 9e 9d f5 d3 ab  35 98 39 59 6c a8 00 01  |".......5.9Yl...|
000001c0  c1 ff 07 fe ff ff 63 96  3b 00 9f 91 7e 11 00 fe  |......c.;...~...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 90 3b 00 00 00  |............;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Can somebody help me out here....

---

### Post by wilee-nilee on 2011-01-24
**Grub 0.97** is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 172241936 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   **/boot/grub/menu.lst** /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

You have a mixture of grub-legacy highlighted and grub2 they don't mix, which do you want? 

It looks as though you used a Ubuntu cd earlier then a Karmic disc to reinstall grub, is this true?

---

### Post by mac4rfree on 2011-01-24
i need only Grub-2.,,, can you guide me how to keep only grub-2 and remove the legacy grub...

Thanks for your help

---

### Post by wilee-nilee on 2011-01-24
Boot into Ubuntu open a terminal run these commands.
```
sudo apt-get purge grub grub-pc grub-common
```
then
```
sudo apt-get install grub-common grub-pc
```

You will both of these first two commands have a gui in the terminal finishing each process follow the instructions, then to be sure grub2 is in the mbr run these two last.

```
sudo grub-install /dev/sda
```
then
```
sudo update-grub
```

Look fpr Windows to be in the terminal after the last command which will list what the grub menu looks like.

---

### Post by mac4rfree on 2011-01-24
Thank you that solved my issue..:)

---

