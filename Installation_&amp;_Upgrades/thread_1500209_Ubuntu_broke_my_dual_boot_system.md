---
title: "Ubuntu broke my dual boot system"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by emeraldknight1977 on 2010-06-02
I run windows XP and Ubuntu on the same system. After the last upgrade Windows fails to load, and shift nullifies my key strokes in Ubuntu [I'm using capslock right now.].

---

### Post by emeraldknight1977 on 2010-06-02
Fixed the shift key issue, but still no Windows. :(

---

### Post by oldfred on 2010-06-03
Post this to see your entire boot configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by emeraldknight1977 on 2010-06-03
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 102158884 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 102158980 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 102149700 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 102158884 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   101,868,164   101,868,102   7 HPFS/NTFS
/dev/sda2         101,868,165   156,296,384    54,428,220   5 Extended
/dev/sda5         101,868,228   153,950,894    52,082,667  83 Linux
/dev/sda6         153,950,958   156,296,384     2,345,427  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
64 heads, 32 sectors/track, 76319 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32   156,299,263   156,299,232   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       e15dc4ca-5e1a-43ac-87bd-1dfa586778f3   ext3                                     
/dev/sda1        26A4C204A4C1D709                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3ebd014c-0174-4490-8caa-c90b8db3b5d0   ext4                                     
/dev/sda6        d9e0bf9c-a9cc-4890-8cb3-d2c7c6ddc1fd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1C740EA1740E7DB0                       ntfs       Big Drive                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        06C43A10C43A030B                       ntfs       USB                           
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=06C43A10C43A030B loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
chainloader	+1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-17-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-19-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-20-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-17-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-19-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-20-generic

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3ebd014c-0174-4490-8caa-c90b8db3b5d0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 26a4c204a4c1d709
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3ebd014c-0174-4490-8caa-c90b8db3b5d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d9e0bf9c-a9cc-4890-8cb3-d2c7c6ddc1fd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  52.3GB: boot/grub/core.img
  55.0GB: boot/grub/grub.cfg
  52.7GB: boot/initrd.img-2.6.31-14-generic
  52.8GB: boot/initrd.img-2.6.31-19-generic
  53.9GB: boot/initrd.img-2.6.31-20-generic
  53.5GB: boot/initrd.img-2.6.31-21-generic
  53.5GB: boot/initrd.img-2.6.32-22-generic
  52.7GB: boot/vmlinuz-2.6.31-14-generic
  52.8GB: boot/vmlinuz-2.6.31-19-generic
  53.8GB: boot/vmlinuz-2.6.31-20-generic
  53.9GB: boot/vmlinuz-2.6.31-21-generic
  53.5GB: boot/vmlinuz-2.6.32-22-generic
  53.5GB: initrd.img
  53.5GB: initrd.img.old
  53.5GB: vmlinuz
  53.9GB: vmlinuz.old

---

### Post by darkod on 2010-06-03
You installed grub2 to the XP partition, ubuntu didn't break anything:

[COLOR=Red]Boot sector info:  Grub 2 is installed in the boot sector of sda1
[/COLOR]
Do the following procedure on /dev/sda1, that's partition #1 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After that it should be fine.

---

