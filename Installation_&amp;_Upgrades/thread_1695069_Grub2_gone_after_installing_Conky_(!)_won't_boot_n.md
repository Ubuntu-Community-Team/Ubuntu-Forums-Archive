---
title: "Grub2 gone after installing Conky (!) won't boot now."
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2011-02-25
As the title says, I installed Conky, and when I rebooted, it sat at a blank screen with cursor... I know Conky shouldn't have this effect (and never has before when I've used it), but it's the only change I made before rebooting.

I tried holding Shift to enter recovery, but no dice. I only have a 9.04 Live CD, so I can't copy Grub2 from that, and I can't burn a copy of 10.10 from the 9.04 live environment... and I can't do a full format/install as the disk has 2tb of 'data' on it :P

I tried installing 9.04 to a weird little 60gb partition I found lying around one of the drives, but the install on that fails at grub-install. I'm lost now.

Could anybody offer any pointers?

---

### Post by NEUR0M4NCER on 2011-02-25
If it's any help, I ran the boot info script to get some info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1   3,776,802,493 3,894,974,368   118,171,876 Linux or Data
/dev/sda2           1,988 3,776,802,492 3,776,800,505 Linux or Data
/dev/sda3   3,894,974,645 3,907,029,134    12,054,490 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073bed

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,930,272,064 2,930,272,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   312,580,095   312,578,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6185a366-e5bd-4d71-95a5-ce94fc971085   ext4                                     
/dev/sda2        aa097cab-be3d-4a4f-9f75-b4756390dd4e   ext4                                     
/dev/sda3        11c42092-84ef-4e57-89d4-500b7478bc0d   swap                                     
/dev/sdb1        1eebe4aa-0c65-4487-a8d3-09181486d34c   ext3                                     
/dev/sdc1        f196faf0-34b2-4c3d-afd8-fef203b0ec62   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6185a366-e5bd-4d71-95a5-ce94fc971085 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=11c42092-84ef-4e57-89d4-500b7478bc0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


1935.5GB: boot/grub/stage2
1935.3GB: boot/initrd.img-2.6.28-11-generic
1935.5GB: boot/vmlinuz-2.6.28-11-generic
1935.3GB: initrd.img
1935.5GB: vmlinuz

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aa097cab-be3d-4a4f-9f75-b4756390dd4e

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		aa097cab-be3d-4a4f-9f75-b4756390dd4e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		aa097cab-be3d-4a4f-9f75-b4756390dd4e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		aa097cab-be3d-4a4f-9f75-b4756390dd4e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		aa097cab-be3d-4a4f-9f75-b4756390dd4e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Chainload into GRUB 2
root		aa097cab-be3d-4a4f-9f75-b4756390dd4e
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		aa097cab-be3d-4a4f-9f75-b4756390dd4e
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set aa097cab-be3d-4a4f-9f75-b4756390dd4e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=aa097cab-be3d-4a4f-9f75-b4756390dd4e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=11c42092-84ef-4e57-89d4-500b7478bc0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/Secondary	ext3	defaults	0	0
/dev/sdc1	/Tertiary	ext4	defaults	0	0

=================== sda2: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  14.7GB: boot/grub/grub.cfg
  76.4GB: boot/grub/menu.lst
1011.5GB: boot/initrd.img-2.6.31-20-generic
  75.0GB: boot/initrd.img-2.6.32-24-generic
 147.4GB: boot/initrd.img-2.6.35-22-generic
 930.6GB: boot/initrd.img-2.6.35-23-generic
  72.3GB: boot/initrd.img-2.6.35-24-generic
 157.1GB: boot/initrd.img-2.6.35-25-generic
 997.5GB: boot/initrd.img-2.6.35-26-generic
1001.3GB: boot/initrd.img-2.6.35-27-generic
 864.3GB: boot/vmlinuz-2.6.31-20-generic
   6.8GB: boot/vmlinuz-2.6.32-24-generic
 135.7GB: boot/vmlinuz-2.6.35-22-generic
 878.9GB: boot/vmlinuz-2.6.35-23-generic
 157.2GB: boot/vmlinuz-2.6.35-24-generic
    .6GB: boot/vmlinuz-2.6.35-25-generic
  22.9GB: boot/vmlinuz-2.6.35-26-generic
1001.2GB: boot/vmlinuz-2.6.35-27-generic
1001.3GB: initrd.img
 997.5GB: initrd.img.old
1001.2GB: vmlinuz
  22.9GB: vmlinuz.old
```

---

### Post by NEUR0M4NCER on 2011-02-25
Found an old 2gb USB, so I'm gonna try booting 9.04 from that, and then burning a copy of 10.10 - still not too sure what I might need to do once that's done though.

---

### Post by srs5694 on 2011-02-25
I'm trying to trace what's what on your installation, but the purpose and use of your partitions is a bit unclear. It looks like:


[list]
[*]/dev/sda1 (a 59 GB partition on your 2 TB disk) is your secondary installation, holding an unknown version of Ubuntu and possibly GRUB 2 files
[*]/dev/sda2 (a 1.9 TB partition on your 2 TB disk) is your main installation, holding Ubuntu 10.10 and both GRUB Legacy and GRUB 2 files
[*]/dev/sdb1 (a 1.5 TB partition on your 1.5 TB disk) is a data partition
[*]/dev/sdc1 (a 160 GB partition on your 160 GB disk) is either a data partition or a tertiary installation, possibly holding Ubuntu 9.04
[*]
[/list]


This is very unclear because the Boot Info Script hasn't reported on the presence of all files for all installations. For instance, it's shown /etc/fstab files on /dev/sda1 and /dev/sda2, a menu.lst (GRUB Legacy) file on /dev/sda2, a grub.cfg (GRUB 2) file on /dev/sda2, and GRUB Legacy boot code in /dev/sdc. If you could say what each of those partitions is *supposed to* be, it might be helpful.

That said, it appears to me that your boot device may have changed in the BIOS; or possibly something removed GRUB code from /dev/sda or /dev/sdb, since it's only present in /dev/sdc. Normally, you'd find GRUB code in the MBR of /dev/sda, but it's not present there.

Thus, as a first step, you might try playing with the boot order in your BIOS. You can usually change the boot device on a one-time basis by hitting some key (typically F2, F10, or F12) during the boot process, or you can enter a BIOS setup utility to make permanent changes.

If that fails, you might try using [Super GRUB Disk](http://www.supergrubdisk.org/) to boot the computer using the GRUB files on your disk. Versions are available for both GRUB Legacy and GRUB 2; try them both. If you can get your system booted, you could try using "sudo grub-install /dev/sda" or "sudo grub-install /dev/sdb" to re-install GRUB (but see the caveat below). There are also ways to re-install GRUB to the MBR using the Ubuntu installer or emergency discs, but I don't recall the precise details for what commands to type.

The fact that you've got both GRUB Legacy and GRUB 2 files installed on /dev/sda2 means that it's impossible to know which boot loader should be associated with that installation. If you can get it booted, you might want to investigate this matter and clean up the /boot/grub directory so that this ambiguity won't complicate recovery efforts like this in the future.

The caveat I mentioned is that your /dev/sda uses the GUID Partition Table (GPT) partitioning method, which requires different GRUB code from the Master Boot Record (MBR) method used on your /dev/sdb and /dev/sdc disks. This needn't be a problem, but GRUB 2 is more reliable on GPT disks if it's got a [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) and your /dev/sda lacks such a partition. Thus, before you attempt to re-install GRUB 2, you should create a BIOS Boot Partition. You can do this with parted or GParted by creating a partition and setting the bios_grub flag; or you can use GPT fdisk (gdisk) and create a partition of type EF02. This partition can be tiny (as small as about 32 KiB), and you've got enough free space at the start of the disk for this, so you shouldn't need to resize any partitions to create a BIOS Boot Partition. Don't create a filesystem on this partition and don't attempt to mount it; GRUB will write to it directly and it's not used under Linux (except when GRUB writes a new version of itself to the partition).

---

### Post by NEUR0M4NCER on 2011-02-25
Thank you so much for your detailed reply!

I actually tried the Super Grub Disk, which is where I think the legacy Grub files have come from. I'll have a look in the Bios, but I don't see how the settings there would have changed (would a failing button battery cause that?).

I'm still trying to get 10.10 onto a CD, it's just come up with an error of some sort:```
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)
```So if I can't get that running, and now that I've got a USB Stick, I'll give the Grub2 version of Super Grub a go (remembering to make a partition for it :) ).

I'll report back to let you know how it goes - thanks again!

---

### Post by srs5694 on 2011-02-25
You don't need to create a BIOS Boot Partition just to try Super GRUB 2 Disk; a BIOS Boot Partition is used as part of the boot process when booting from hard disk, but if you're booting from a Super GRUB Disc CD, you're booting from CD, not from the hard disk. The disc just searches for and uses the grub.cfg file(s) on your hard disk to determine what kernel to boot. Once you've booted and want to re-install GRUB to the hard disk, a BIOS Boot Partition will be helpful.

I'm not sure if a failing battery could cause BIOS settings to become corrupted. I know they can be damaged by problems in OSes or perhaps boot loaders, although such damage is rare. They also sometimes get changed by random factors like cosmic rays. (Really, I'm serious.)

---

### Post by NEUR0M4NCER on 2011-02-25
A combination of changing where the bios looked for boot, as well as a fresh install og 10.10 finally did the trick (I put it on that old 60gb partition, so I can just link to all my old data on the other partitions - probably needed a fresh install anyways.

Thank you for your help, sorry I didn't go the hard-core route of figuring this out, but it's the family 'puter... :D

Regards!

---

