---
title: "Ubuntu 10 Grub2 can't see my sda7"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by johncc on 2011-01-01
I have been trying to install from LiveCD to my sda7.  Grub then complains that the partition is not found.

I think the gist of the problem is that partitions are:
```
root@vaio:/home/john# fdisk -l /dev/sda

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04322fce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         462     3710983+  83  Linux
/dev/sda2             463         705     1951897+  82  Linux swap / Solaris
/dev/sda3             706        4474    30274492+   7  HPFS/NTFS
/dev/sda4            4475       24321   159420997    f  W95 Ext'd (LBA)
/dev/sda5            4475        4863     3124611   83  Linux
/dev/sda6            4864       18236   107418591    7  HPFS/NTFS
/dev/sda7   *       18237       20060    14651248+  83  Linux
/dev/sda8           20061       21884    14651248+  83  Linux
/dev/sda9           21885       24321    19575171    b  W95 FAT32
root@vaio:/home/john#

```

but if when booting I go to the Grub command line and "ls" I only get:

```
GNU GRUB version 1.98-20100804-5ubuntu3
grub> ls
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)
grub>

```

I can boot fine on the Ubuntu that I installed on sda1 (but I would like a bigger partition, like sda7).  

In the ubuntu grub2 help ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) I read:
> You may have a buggy BIOS and the location of your /boot/* files is not under the 1024 cylinder boundary. Create a small partition on the beginning of the disk, mount it as /mnt/b, cp -av /boot/* /mnt/b; umount /mnt/b; mount /dev/small_partition /boot; grub-install /dev/<device>. 

I tried this but it didn't work any better.  (Not sure I did it right though, I booted from LiveCD when I did it)

Is there some way I can have grub load itself from sda1, but then end up with "/" being mounted from sda7?

Thank you,
John

P.S. I can post results from "boot_info_script" if that will help.

---

### Post by Quackers on 2011-01-02
The boot script output may help to clarify things.

---

### Post by johncc on 2011-01-02
To recap, I have 9 partitions, but Grub only sees 3 of them
```
GNU GRUB version 1.98-20100804-5ubuntu3
grub> ls
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)
grub>

```

Here are the results from bootinfo script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     7,422,029     7,421,967  83 Linux
/dev/sda2           7,422,030    11,325,824     3,903,795  82 Linux swap / Solaris
/dev/sda3          11,325,825    71,874,809    60,548,985   7 HPFS/NTFS
/dev/sda4          71,874,871   390,716,864   318,841,994   f W95 Ext d (LBA)
/dev/sda5          71,874,873    78,124,094     6,249,222  83 Linux
/dev/sda6          78,124,158   292,961,339   214,837,182   7 HPFS/NTFS
/dev/sda7    *    292,961,403   322,263,899    29,302,497  83 Linux
/dev/sda8         322,263,963   351,566,459    29,302,497  83 Linux
/dev/sda9         351,566,523   390,716,864    39,150,342   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        29735fe1-1c02-4c2d-b407-57a28d2100c0   ext4                                     
/dev/sda2                                               swap                                     
/dev/sda3        2A14E83714E80821                       ntfs       New Volume                    
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f374d5cc-b030-417e-80e8-97aabd53d787   ext3                                     
/dev/sda6        8EA0F6E7A0F6D4A5                       ntfs       New Volume                    
/dev/sda7        d79aa28c-c125-4bc4-a15f-83bc2d4a5f17   ext4                                     
/dev/sda8        c799fc5f-8584-4f53-91a7-607c4cf1f0ef   ext3                                     
/dev/sda9        4460-E7FF                              vfat       SHAREFAT                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
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
	search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=29735fe1-1c02-4c2d-b407-57a28d2100c0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=29735fe1-1c02-4c2d-b407-57a28d2100c0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=29735fe1-1c02-4c2d-b407-57a28d2100c0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=29735fe1-1c02-4c2d-b407-57a28d2100c0 ro single 
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
	search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 29735fe1-1c02-4c2d-b407-57a28d2100c0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2a14e83714e80821
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda6)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8ea0f6e7a0f6d4a5
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux /boot/vmlinuz-2.6.35-22-generic root=/home/ubuntu/aufs ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux /boot/vmlinuz-2.6.35-22-generic root=/home/ubuntu/aufs ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux /boot/grub/core.img 
}
menuentry "Ubuntu 10.10, memtest86+ (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux /boot/memtest86+.bin 
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
   2.3GB: boot/grub/grub.cfg
   1.9GB: boot/initrd.img-2.6.35-22-generic
   1.9GB: boot/initrd.img-2.6.35-24-generic
   1.5GB: boot/vmlinuz-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-24-generic
   1.9GB: initrd.img
   1.9GB: initrd.img.old
    .2GB: vmlinuz
   1.5GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

C:\wubildr.mbr = "Ubuntu"


================================ sda6/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

C:\wubildr.mbr = "Ubuntu"


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=/home/ubuntu/aufs ro

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/home/ubuntu/aufs ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/home/ubuntu/aufs ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		(hd0,0)
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d79aa28c-c125-4bc4-a15f-83bc2d4a5f17 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d79aa28c-c125-4bc4-a15f-83bc2d4a5f17 ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set d79aa28c-c125-4bc4-a15f-83bc2d4a5f17
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2a14e83714e80821
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda6)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8ea0f6e7a0f6d4a5
	drivemap -s (hd0) ${root}
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=d79aa28c-c125-4bc4-a15f-83bc2d4a5f17 /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 158.8GB: boot/grub/core.img
 150.2GB: boot/grub/grub.cfg
 159.0GB: boot/grub/menu.lst
 158.8GB: boot/grub/stage2
 152.8GB: boot/initrd.img-2.6.35-22-generic
 151.0GB: boot/vmlinuz-2.6.35-22-generic
 152.8GB: initrd.img
 151.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


```

---

### Post by oldfred on 2011-01-02
I am not sure what you mean partition not found. You have full installs in sda1 & sda7. Your install in sda1 has entries for the install in sda7.

It looks like you tried installing old grub legacy into sda7. A classic chainboot entry has to be to grub installed into a partition which you do not have.

If you want to create your own boot stanza this works, but I do not know why the ones the osprober created do not work for you.

You would have to add this to your 40_custom in sda1.

menuentry "Install on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}

---

### Post by johncc on 2011-01-02
Thanks for your reply!
> **oldfred said:**
> I am not sure what you mean partition not found. You have full installs in sda1 & sda7. Your install in sda1 has entries for the install in sda7.

Yes, and when I select the entry for sda7 it immediately says:
```

error:no such device: d7aa2-bc125-etc-etc-etc
error: no such partition.
error: you need to load the kernel first.

```
I also tried using the grub "minimal editor" to specify /dev/sda7 instead of the UUID d7aa2-etc-etc, but it gave the same error message. 

If I drop to the grub command line ("c") and type 'ls' it only shows three partitions "(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)".  That's what I mean by grub2 "not finding" my partition. ?

> 
It looks like you tried installing old grub legacy into sda7. A classic chainboot entry has to be to grub installed into a partition which you do not have.

Yes, after having trouble booting from the sda7 I read somewhere to revert to legacy grub.  I tried that and had trouble as well (maybe because I was trying to do it from LiveCD, I'm not sure).  Finally I installed on sda1 which does boot ok (but is smaller than I would like).

---

### Post by drs305 on 2011-01-02
Have you checked to see how large the BIOS thinks the drive is? If the BIOS is limited to seeing only 137GB of the drive the remainder would be invisible to it. During boot access your BIOS and see what it reports for the drive size - it should be around 200GB.

If it's not see if there is a setting you can change or check to see if your manufacturer has an update to your BIOS.

Note: After booting your OS may see the entire 200GB, but that doesn't necessarily mean that the BIOS can see all of it.

---

### Post by johncc on 2011-01-02
> **drs305 said:**
> Have you checked to see how large the BIOS thinks the drive is? If the BIOS is limited to seeing only 137GB of the drive the remainder would be invisible to it. During boot access your BIOS and see what it reports for the drive size - it should be around 200GB.


In "Auto" mode my award bios reports:
```
Cylinders: 1024
Heads: 255
Sector: 63
CHS Capacity: 8422MB
Maximum LBA Capacity: 8455MB
```
It will allow me to put in "user specified" CHS values, but what values do I use?  Do I put in the 24321 Cylinders per the boot info report?

Thanks!
John

---

### Post by oldfred on 2011-01-02
Is this computer very old or do you not have LBA turned on? Related to BIOS limits in drs305's post:

[http://members.iinet.net.au/~herman546/p15.html#18]("http://members.iinet.net.au/%7Eherman546/p15.html#18")
```
8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
  33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
  137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)

```

---

### Post by johncc on 2011-01-02
> **oldfred said:**
> Is this computer very old or do you not have LBA turned on? Related to BIOS limits in drs305's post:

[http://members.iinet.net.au/~herman546/p15.html#18]("http://members.iinet.net.au/%7Eherman546/p15.html#18")
```
8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
  33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
  137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)

```

I guess its about circa 2000 bios. LBA seems to be on, but any option I choose indicates around 8GB.

But, I put in manual CHS (24321 cyl), bios said 200gb.  But when I booted (even sda1) the box froze up.


As I mentioned in OP, 
In the ubuntu grub2 help ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) I read:
> 
You may have a buggy BIOS and the location of your /boot/* files is not under the 1024 cylinder boundary. Create a small partition on the beginning of the disk, mount it as /mnt/b, cp -av /boot/* /mnt/b; umount /mnt/b; mount /dev/small_partition /boot; grub-install /dev/<device>.

I tried per this cryptic description but I don't think I did it right, I had booted from LiveCD when I did it.  IIRC the grub-install complained that I had no root device (but I've slept twice since then, etc).

Is there some way I can have grub2 load itself and kernel from sda1, but then the kernel mounts "/" from sda7?  Before, I had even tried installing from LiveCD with /boot on sda1 and / on sda7, thinking it would achieve this.  

I can reinstall on either of these partitions (sda1, sda7) if anybody have any suggestions.  But I wanted to hang onto the NTFS partitions.

Thanks!
John

---

### Post by drs305 on 2011-01-02
Perhaps the easiest thing to do would be to turn your sda2 (swap) partition into a /boot partition for your sda7 installation. That way you will always have a boot partition within your system's BIOS limitations. It will also mean that you won't have to do a lot of time-consuming repartitioning or resizing. It will much larger than a /boot partition needs to be, but you can't divide it due to the 4 primary partition limitation.

You would need to:
1. Reformat /dev/sda2 to ext3 or ext4

2. Copy your sda7 boot files into this partition. (Don't make a /boot folder, everything would go directly into the folder as it appears under /boot now). Do this with the first two commands later and use Nautilus to move the contents of sda7's /boot to sda2's /.

3.Add the /boot partition to your sda7 fstab and for the moment comment out (put a # symbol at the start of the swap line).

4.Install Grub2 from the LiveCD with the following commands:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda2 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Later you can shrink your last partition and add a swap partition.

If you have questions, ask before you run these procedures. You also might want to wait to see if others have better ideas.  ;-)

Added: I didn't recognize the quote from the community doc and had to go look it up. Then I realized it's an open doc that can be amended by any of the Ubuntu doc people and I wasn't the author of that section. I admit it's a bit confusing and will see if I can rewrite it at some point.

---

### Post by johncc on 2011-01-02
Ok, I think I understand.  But

1) I have a fresh, running, ubuntu install on sda1.  I can boot into it to do the below instructions, instead of LiveCD.  Correct?

2) So I will do this:
```
sudo su
swapoff -a

# format sda2
mkfs -t ext4 /dev/sda2  # or maybe I'll use gparted to do it

# mounts for copy
mkdir /mnt/s7; mount /dev/sda7 /mnt/s7
mkdir /mnt/s2; mount /dev/sda2 /mnt/s2

# edit /mnt/s7/etc/fstab, disable swap and add /dev/sda2 as /boot

# copy boot and grub directories from sda7 to sda2
cp -avr /mnt/s7/boot/* /mnt/s2

# arrange mounts for grub-install
umount /mnt/s7; umount /mnt/s2
mount /dev/sda7 /mnt
mount /dev/sda2 /mnt/boot

grub-install --root-directory=/mnt /dev/sda

# cross fingers and reboot
```

Thanks, I will try this later tonight.

Cheers,
John

P.S. About the Grub2 help page.  I understand that you (drs305) didn't write those "cryptic instructions", but shouldn't it have been "cp -avr /boot/* /mnt/b" instead of "cp -av /boot/* /mnt/b".  Maybe this tripped me up before.

---

### Post by drs305 on 2011-01-02
> **johncc said:**
> Ok, I think I understand.  But

1) I have a fresh, running, ubuntu install on sda1.  I can boot into it to do the below instructions, instead of LiveCD.  Correct?Thanks, I will try this later tonight.

Cheers,
John

P.S. About the Grub2 help page.  I understand that you (drs305) didn't write those "cryptic instructions", but shouldn't it have been "cp -avr /boot/* /mnt/b" instead of "cp -av /boot/* /mnt/b".  Maybe this tripped me up before.

Yes, you can do this from your sda1 Ubuntu.

The command sequence is very nicely done. One other thing is that after you copy the /boot folder contents you should (re)move the existing sda7 boot files. I believe these files would be hidden when the /boot partition is mounted but it would be better if they just aren't there.

I've rewritten the G2 section in question. I actually removed the specific instructions since there was another community doc (now referenced) on how to create a separate /boot partition. Unfortunately that page is pretty old and needs work, but I did update it for Grub2. I'll probably take another look at the Grub2 page as well since there have been other additions since I wrote it. I'll try to ensure it makes sense after getting a good night's sleep.

Yes, you should include the "-r" switch since there are folders such as 'grub' and 'locale' within /boot, or you can simply use the -a switch.

Just one disclaimer: You are wasting space by leaving the /boot partition as large as it is. You could shrink it a bit and add some space to the end of sda1. What I proposed is just the easiest way to do it.

I'll check back tomorrow and hopefully read of your success.

---

### Post by johncc on 2011-01-03
Hmmm, it did the same thing, as when I had first tried install from LiveCD fresh with / as sda7 and /boot as sda1:
```
error: no such device: d79aa28c-c125-etc-etc
error: no such partition.
error: you need to load the kernel first

```So when I 'e' the boot entry I see
```
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d79aa28c-c125-etc-etc
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d79aa28c-c125\
-etc-etc ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic
```

What is it that's supposed to tell it that /boot is on sda2?

I find that if I edit like this, it will boot:
```
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
linux (hd0,msdos2)/vmlinuz-2.6.35-22-generic root=UUID=d79aa28c-c125\
-etc-etc ro quiet splash
initrd (hd0,msdos2)/initrd.img-2.6.35-22-generic
```

Thanks for your help drs305!  I will be at work tomorrow but may pick it back up in the evening.

Cheers,
John

---

### Post by drs305 on 2011-01-03
> **johncc said:**
> 
What is it that's supposed to tell it that /boot is on sda2?


We are getting close! 

First, you might want to run the following command just to ensure you have the current, non-cached UUIDs:
```
sudo blkid -c /dev/null
```

Here is the original menuentry. 
[COLOR="DarkRed"]**The areas in dark red should point to the boot partition.**[/COLOR]
**[COLOR="Navy"]The areas in dark blue should point to / .[/COLOR]**

```
recordfail
insmod part_msdos
insmod ext2
[B][COLOR="DarkRed"]set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d79aa28c-c125-etc-etc
linux /boot/vmlinuz-2.6.35-22-generic[/COLOR][/B] **[COLOR="Navy"]root=UUID=d79aa28c-c125-etc-etc[/COLOR]** ro quiet splash
**[COLOR="DarkRed"]initrd /boot/initrd.img-2.6.35-22-generic[/COLOR]**
```

The 'search' and 'set root=' entries should point to the boot partition; they provide the base path for subsequent lines (more on this later).
The 'root=UUID=' should point to /.

So why did your first menuentry fail? 
'search' and 'set root' both pointed to / and sda7.
'linux' and 'initrd' were both based on a boot address in /, so the files were not found.

Why did your second attempt work?
> 
set root='(hd0,msdos7)'
linux (hd0,msdos2)/vmlinuz-2.6.35-22-generic root=UUID=d79aa28c-c125-etc-etc ro quiet splash
initrd (hd0,msdos2)/initrd.img-2.6.35-22-generic

Your 'set root=' is still incorrect, but because you used specific paths in 'linux' and 'initrd' to the boot partition, G2 found the files.

What should it look like:
> 
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,**msdos2**)'
search --no-floppy --fs-uuid --set **<boot partition UUID>**
linux /vmlinuz-2.6.35-22-generic root=UUID=d79aa28c-c125-etc-etc ro quiet splash
initrd /initrd.img-2.6.35-22-generic

A couple of observations about this entry:
1, Note the 'linux' and 'initrd' lines do not contain '/boot' since the /boot partition is mounted directly on sda2.
2. The standard generic entry of 'linux /vmlinuz' would not work with the menu set up this way since there is no 'vmlinuz' shortcut in the /boot directory.

Once you successfully boot into your sda7 installation, run "sudo update-grub" and then check /boot/grub/grub.cfg to see what kind of menuentry it generated. It should make one that boots. 

If the auto-generated menuentry fails:
Copy the menuentry above or what you made work and paste it into /etc/grub.d/40_custom below the existing lines.
Run "sudo update-grub" again to incorporate the custom menu.

---

### Post by johncc on 2011-01-03
> **drs305 said:**
> 
[COLOR="DarkRed"]**The areas in dark red should point to the boot partition.**[/COLOR]
**[COLOR="Navy"]The areas in dark blue should point to / .[/COLOR]**

```
recordfail
insmod part_msdos
insmod ext2
[B][COLOR="DarkRed"]set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set d79aa28c-c125-etc-etc
linux /boot/vmlinuz-2.6.35-22-generic[/COLOR][/B] **[COLOR="Navy"]root=UUID=d79aa28c-c125-etc-etc[/COLOR]** ro quiet splash
**[COLOR="DarkRed"]initrd /boot/initrd.img-2.6.35-22-generic[/COLOR]**
```

The 'search' and 'set root=' entries should point to the boot partition; they provide the base path for subsequent lines (more on this later).
The 'root=UUID=' should point to /.


This is the Aha moment.  I didn't realized that 'set root=' should be pointing to the 'root for the boot files', i.e. the boot partition.  I thought it was setting the root for the kernel.  This makes much more sense to me now.  (At one point I was literally thinking, "shouldn't there be a 'set BOOT=(hd0,msdos2)'  :) )

update:  Hey it worked!!  I did update-grub and now I can boot all my partitions!  I carved out a 1GB swap partition and enabled it.  Thanks!

My last question is, shouldn't I have expected to have achieved the same result when I did the fresh install from LiveCD, manual partitioning with / at sda7 and /boot at /sda1?  I did this early on, and it did produce a /boot partition with the linuz, initrd, grub/ etc.  But maybe I missed a step, because it seemed to be wanting to get the boot files from /sda7.

Cheers,
John

---

