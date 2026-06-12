---
title: "Trying to install on external drive on laptop"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by skorda on 2008-06-13
Hello,

I am a database developer who is trying to teach myself Linux :).  I figured I'd start with something easy (Ubuntu) by installing it on a USB external drive attached to my Gateway laptop.  The internal drive has Windows Vista :evil:.  The issue is I am trying to keep my internal drive clean and not have the boot loader modify my MBR.  My BIOS allows me to boot directly from a USB HD.

However, no matter how I install Ubuntu on /dev/sdb (my external USB drive), all I get is a black screen with GRUB on the upper left corner whenever I boot it.  I can't type anything and no other error message is given.  I've tried editing the menu.lst and installing no boot loader.  Surely, there must be a way to do this?  Please help!

For convenience, I've printed my fdisk info and slightly modified menu.lst file below (it didn't work unmodified either):confused::

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x082e082d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11661    93666951   83  Linux
/dev/sdb2           11662       12161     4016250    5  Extended
/dev/sdb5           11662       12161     4016218+  82  Linux swap / Solaris


# menu.lst - See: 

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		1
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=50226819-a31b-4cc4-96af-657b4d6bcca3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## title		Ubuntu 8.04, kernel 2.6.24-16-generic
## root		(hd1,0)
## kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=50226819-a31b-4cc4-96af-657b4d6bcca3 ro quiet splash
## initrd		/boot/initrd.img-2.6.24-16-generic
## quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=50226819-a31b-4cc4-96af-657b4d6bcca3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

---

### Post by Pumalite on 2008-06-13
In menu.lst; make 'groot' and 'root': (hd0,0)

---

### Post by skorda on 2008-06-13
Thanks, but unfortunately that did not work.

I still get the GRUB screen.

I am getting a feeling that I need to write something more to the external drive (hd1).  Like maybe GRUB doesn't know where to go or something?  Just guessing.:confused:

---

### Post by meierfra. on 2008-06-13
Get Supergrub (see my signature) and see whether  supergrub can detect your Ubuntu partition:
[URL="http://www.supergrubdisk.org/wiki/USB_Boot"]
http://www.supergrubdisk.org/wiki/USB_Boot[/URL]

If Supergrub can not detect  the ubuntu partition, you will have to create a separate boot partition an the internal drive.

If Supergrub does detect the Ubuntu partition, then it also should be able to boot Ubuntu. In this case you should be able to fix your problem  by reinstalling grub and/or editing menu.lst

In any case  just come back here for more help.

---

