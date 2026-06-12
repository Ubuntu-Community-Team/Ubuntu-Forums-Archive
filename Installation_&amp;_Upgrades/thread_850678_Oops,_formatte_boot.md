---
title: "Oops, formatte /boot"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by SkonesMickLoud on 2008-07-05
Hey all, today I attempted to add Windows XP to my current Ubuntu 8.04 installation, and I inadvertently formatted over my /boot (former sda1).  Now Gparted doesn't see any partitions, and shows an unallocated space of 149.05 Gb (out of ~250 Gb) on sda.  The Ubuntu install disk also doesn't see any partitions, so simply reinstalling Ubuntu wouldn't work, as I don't want to over write my /home.

My data seems to all be there, as I can still mount all of the partitions through the LiveCD.

Is there any way I can "rebuild" /boot?

Here's the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 /               reiserfs notail,relatime 0       1
# /dev/sda1
UUID=0effa667-bf00-442a-8baa-8eff4b143a3e /boot           reiserfs notail,relatime 0       2
# /dev/sda3
UUID=53dc1bb2-8821-42ee-a4fd-2dd362173281 /home           ext3    relatime         0       2
# /dev/sda5
UUID=ea6a74d0-18ef-485f-8c81-292d6b604c12 none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

And the latest backup of my menu.lst:

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
# kopt=root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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



#title		Ubuntu 8.04, kernel 2.6.25.9-ultimate
#root		(hd0,0)
#kernel		/vmlinuz-2.6.25.9-ultimate root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro quiet splash
#initrd		/initrd.img-2.6.25.9-ultimate
#quiet

#title		Ubuntu 8.04, kernel 2.6.25.9-ultimate (recovery mode)
#root		(hd0,0)
#kernel		/vmlinuz-2.6.25.9-ultimate root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro single
#initrd		/initrd.img-2.6.25.9-ultimate

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=c55105e6-b97e-4662-9fa0-f7895896d6c3 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Both of these files are inside of my current Ubuntu install partitions.  fstab is in my / partition, and the menu.lst is a backup in my /home.

---

### Post by logos34 on 2008-07-06
You're going to have to use TestDisk from the ubuntu live cd to fix the partition table.  Then run grub-install.

>system>admin>software sources>enable **universe** repository

sudo apt-get install testdisk

sudo testdisk

Read the documentation [here]("http://www.cgsecurity.org/wiki/TestDisk") and [here]("http://www.users.bigpond.net.au/hermanzone/p21.html").

When finished, use Gparted to re-format as reiserfs.

Then, remount / and /boot:

sudo mkdir /media/sda4
sudo mount -t ext3 /dev/sda4 /media/sda4
sudo mount -t reiserfs /dev/sda1 /media/sda4/boot
sudo mount --bind /dev /media/sda4/dev
sudo chroot /media/sda4
sudo grub-install --root-directory=/boot /dev/sda1
(or maybe just 'sudo grub-install /dev/sda1')
sudo update-grub

Hope that works, though TBH never tried it exactly like that (with separate /boot mounted in /) from the live cd.

---

