---
title: "Can't boot into XP after Lucid upgrade"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by cap10xb1s on 2010-06-07
I have tried various things suggested on Ubuntu Forums but still cannot boot into Windows XP following uograde from karmic to lucid.

It comes up on the grub list at the start but when I select it I just get a flashing cursor. Dont know grub well at all so would appreciate some diagnostic advice and guidance

Below is the results I get from a boot info script

Brendan
----------------------
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 28491847 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 28475455 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,279,609   488,279,547   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,279,609   488,279,547  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1047-19FD                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7174fee4-af05-44ea-a7a4-a5b43d834200   ext3                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /media/1047-19FD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7174fee4-af05-44ea-a7a4-a5b43d834200

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		7174fee4-af05-44ea-a7a4-a5b43d834200
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		7174fee4-af05-44ea-a7a4-a5b43d834200
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		7174fee4-af05-44ea-a7a4-a5b43d834200
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		7174fee4-af05-44ea-a7a4-a5b43d834200
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Chainload into GRUB 2
root		7174fee4-af05-44ea-a7a4-a5b43d834200
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		7174fee4-af05-44ea-a7a4-a5b43d834200
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
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
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7174fee4-af05-44ea-a7a4-a5b43d834200
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1047-19fd
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=7174fee4-af05-44ea-a7a4-a5b43d834200 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  14.5GB: boot/grub/core.img
  14.5GB: boot/grub/grub.cfg
  14.5GB: boot/grub/menu.lst
  14.5GB: boot/initrd.img-2.6.31-20-generic
  14.5GB: boot/initrd.img-2.6.32-22-generic
  14.5GB: boot/vmlinuz-2.6.31-20-generic
  14.5GB: boot/vmlinuz-2.6.32-22-generic
  14.5GB: initrd.img
  14.5GB: initrd.img.old
  14.5GB: vmlinuz
  14.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by wilee-nilee on 2010-06-07
So you have grub in the sda1 partition. If you could edit the script with code tags it will make it easier to read.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
 This will take a more experienced user to diagnose. sda1 reads as fat32 so I'm not sure but others will be

---

### Post by arrange on 2010-06-07
You have Grub2 installed in the Win boot sector (*sda1*), which you now have to repair.

For more info see
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)

---

### Post by darkod on 2010-06-07
In your setup, best is:

Turn the computer off. Disconnect the ubuntu disk. Boot with only the windows disk connected and use the XP install cd to boot with it. Repair the boot process and mbr with the cd, if you need instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After that shutdown, connect the ubuntu disk, start and go into BIOS and make the ubuntu disk first option to boot from. You should see grub loading.

Besides /boot/grub/grub.cfg you have also /boot/grub/menu.lst present. Usually you have this if you started the process to upgrade grub legacy to grub2, but never finished it. Did you upgrade to 10.04 from 9.10? What grub version did you use with 9.10?

If you have a mix of grub1 and grub2, it would add more confusion. That's why if you started upgrade process from grub legacy to grub2 while running 9.10, you should have completely finished it and remove menu.lst, before upgrading the OS to 10.04.

All of that is hypothetical now, I don't know how things developed and what were you running before.

---

### Post by cap10xb1s on 2010-06-07
> **arrange said:**
> You have Grub2 installed in the Win boot sector (*sda1*), which you now have to repair.

For more info see
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)
Hi Arrange - I tried that already and it did't work

---

### Post by darkod on 2010-06-07
> **cap10xb1s said:**
> Hi Arrange - I tried that already and it did't work

Instead of reading through the whole thread, the fix is here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Is that what you tried? You need to perform that procedure on /dev/sda1, so that's partition #1 on disk /dev/sda.

Alternatively, do as I suggested in my previous post.

---

### Post by cap10xb1s on 2010-06-07
Thats what I've tried several times. I've managed a workaround now by installing grub1 and then using chainloader to manually boot into either partition as described in the section "Indirect bootby chainloading from [here]("http://www.justlinux.com/forum/showthread.php?t=152790")"

---

