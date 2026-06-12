---
title: "Dedicated grub partition, 10.4 boot error 15, file not found"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by pieguy on 2010-05-06
I have a separate partition just for grub legacy(this does NOT contain kernels) that boots up the OS's.

I have 2 8.10's and a 10.4 I just installed on the hard drive.  I have got the 2 8.10's to boot but even after configuring and rechecking the menu.lst and fstab for accuracy the 10.4 will "Error 15: File not found" when I select it.  

I did NOT install the boot loader(step 8 of install I clicked advanced and uncheck install bootloader) when I installed 10.4 so there shouldnt be a conflict with grub2, there is an empty grub folder on the 10.4.

From the looks of my menu.lst, it looks correct but still doesnt work.  I'm using the correct UUID so that cant be it.

This is the menu.lst on my dedicated partition
```
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
timeout		10

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
# kopt=root=UUID=be2bf5f4-a3e8-42d5-a729-b34937673d0d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=be2bf5f4-a3e8-42d5-a729-b34937673d0d

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

title		Ubuntu 8.10, kernel 2.6.27-17-generic
uuid		2b169487-fb28-4210-853c-28cd4066c4c1
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=2b169487-fb28-4210-853c-28cd4066c4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
uuid		2b169487-fb28-4210-853c-28cd4066c4c1
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=2b169487-fb28-4210-853c-28cd4066c4c1 ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 8.10, memtest86+
uuid		2b169487-fb28-4210-853c-28cd4066c4c1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

[B]title		Ubuntu 10.4, kernel 2.6.32-21-generic
uuid		ff6782f0-65ec-4c00-8109-f462ab819830
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=ff6782f0-65ec-4c00-8109-f462ab819830 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.4, kernel 2.6.32-21-generic (recovery mode)
uuid		ff6782f0-65ec-4c00-8109-f462ab819830
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=ff6782f0-65ec-4c00-8109-f462ab819830 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic[/B]

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		be2bf5f4-a3e8-42d5-a729-b34937673d0d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=be2bf5f4-a3e8-42d5-a729-b34937673d0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		be2bf5f4-a3e8-42d5-a729-b34937673d0d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=be2bf5f4-a3e8-42d5-a729-b34937673d0d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic


```

This is the fstab located in etc/fstab of the 10.4
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=**ff6782f0-65ec-4c00-8109-f462ab819830** /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7f1ef3eb-0dab-408b-ada8-10ed51b19fb0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I did have to change the UUID for the OS partition in fstab because it was a different UUID.  Using blkid I got the current UUID.

---

### Post by pieguy on 2010-05-07
The way I resolved this was to install a 2nd copy of 10.4 which setup the first copy of 10.4 to boot.  Once in the first 10.4, I reverted the grub2 to grub legacy, added its menu.lst info to the menu.lst on the dedicated grub partition and wrote the location of the grub partition to the mbr.

So I dont know how to get a os with grub2 to work this way but I was able to revert it to grub and was able to get it to work then.

---

