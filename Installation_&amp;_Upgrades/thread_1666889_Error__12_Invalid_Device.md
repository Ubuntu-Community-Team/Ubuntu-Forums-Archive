---
title: "Error  12 Invalid Device"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by 99digit on 2011-01-14
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /grub.cfg /boot/grub/grub.cfg 
                       /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 43006068.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,099,672    39,099,610  83 Linux
/dev/sda2          39,100,414   312,576,704   273,476,291   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5          39,100,416    43,005,951     3,905,536  82 Linux swap / Solaris
/dev/sda6         177,405,858   312,576,704   135,170,847   7 HPFS/NTFS
/dev/sda3    *     43,006,068   177,405,794   134,399,727   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f8748588-d670-46bb-a7bd-a9fb5c6ec61f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        8C3055F43055E5AC                       ntfs       New Volume                    
/dev/sda5        a3fb1c6d-cadd-4e47-bfc0-35287e462ad5   swap                                     
/dev/sda6        FA8861158860D225                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/New_Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/New_Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8748588-d670-46bb-a7bd-a9fb5c6ec61f

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro  single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		f8748588-d670-46bb-a7bd-a9fb5c6ec61f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1

================================ sda1/grub.cfg: ================================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f8748588-d670-46bb-a7bd-a9fb5c6ec61f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8748588-d670-46bb-a7bd-a9fb5c6ec61f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/	ext4	errors=remount-ro	0	1
/dev/sda3	/media/New_Volume	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda6	/media/New_Volume_	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda5	none	swap	sw	0	0
#/dev/sdb1      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdc1      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
   3.0GB: boot/grub/menu.lst
  17.4GB: boot/grub/stage2
  18.3GB: boot/initrd.img-2.6.32-21-generic
  18.5GB: boot/initrd.img-2.6.32-27-generic
  18.1GB: boot/vmlinuz-2.6.32-21-generic
  18.3GB: boot/vmlinuz-2.6.32-27-generic
    .1GB: grub.cfg
  18.5GB: initrd.img
  18.3GB: initrd.img.old
  18.3GB: vmlinuz
  18.1GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

What should i do, really confused now.

Ubuntu 10.04

---

### Post by 99digit on 2011-01-14
bump need help with this asap, sorry if people here dnt like bumped threads but really in a fix here :confused: :sad:

---

### Post by 99digit on 2011-01-14
bump need help with this asap, sorry if people here dnt like bumped threads but really in a fix here :confused: :sad:

---

### Post by 99digit on 2011-01-14
bump need help with this asap, sorry if people here dnt like bumped threads but really in a fix here :confused: :sad:

i tried to delete the extra messages but couldnt find a delete button sorry yet again

---

### Post by 99digit on 2011-01-15
(hd0,2) does not atleast give an error. but booting wont go further than 
Starting Up ....

and the cursor blinking below it. what can be the problem and solution to it?

---

