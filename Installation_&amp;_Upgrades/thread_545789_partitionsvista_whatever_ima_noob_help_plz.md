---
title: "partitions/vista whatever ima noob help plz"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by Shotty69 on 2007-09-08
hi guys so today i thought i would test out ubuntu on my desktop that ive had for 6 months which was running windows vista home premium, ive been messing with it all night trying to get  it to load windows vista again (i really do hope i didnt remove it, i could cry) i tryed the boot menu thing this is what mine has in it

> v# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		1

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
# kopt=root=UUID=0df48a42-1d87-4a69-b2a0-4cd5896976f3 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0df48a42-1d87-4a69-b2a0-4cd5896976f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0df48a42-1d87-4a69-b2a0-4cd5896976f3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0df48a42-1d87-4a69-b2a0-4cd5896976f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0df48a42-1d87-4a69-b2a0-4cd5896976f3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

i changed default to "1" as a lot of sites recommended i did, yes i edited the file with run cmd too. PLEASEPLEASE HELP ME GET VISTA BACK!!

---

### Post by Shotty69 on 2007-09-08
i forgot to mention now i go to load any boot disk or whatever w/ bios like lets say i do the vista OS disk and it will load and just sit there, ubuntu does this too now, and the XP disk i tryed gives me a bluescreen after everything loads

---

### Post by confused57 on 2007-09-08
If you can boot into your installed Ubuntu, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

This should show if your Vista partition is still there.

---

### Post by Shotty69 on 2007-09-08
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29258   235014853+  83  Linux
/dev/sda2           29259       30394     9124920    5  Extended
/dev/sda5           29259       30394     9124888+  82  Linux swap / Solaris

im assuming its gone :(

---

### Post by confused57 on 2007-09-08
> **Shotty69 said:**
> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29258   235014853+  83  Linux
/dev/sda2           29259       30394     9124920    5  Extended
/dev/sda5           29259       30394     9124888+  82  Linux swap / Solaris

im assuming its gone :(

Unfortunately, there doesn't appear to be a ntfs partition on your hard drive.  I don't really know why you're not able boot your install disks...if I find anything, I'll let you know.

---

### Post by Shotty69 on 2007-09-08
si, well i did just get the vista install disk to work TY GOD IM ON VISTA AS IM TYPING THIS, ty for all of your help unfortanatly this whole incident probally scared me away from ubuntu for a while

---

### Post by confused57 on 2007-09-08
Good to hear you were able to get Vista reinstalled.  If you decide you want to try Ubuntu sometime in the future, there is a program called EasyBCD that sets up booting Ubuntu from the Vista bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

The only thing different you would do is install grub's IPL to the root partition, rather than the mbr.  Also, just to be on the safe side, I would recommend resizing your Vista partition using Vista's built-in partitioner:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Sorry you had a bad first impression with Ubuntu.

---

### Post by karl_stade on 2007-09-08
> **Shotty69 said:**
> si, well i did just get the vista install disk to work TY GOD IM ON VISTA AS IM TYPING THIS, ty for all of your help unfortanatly this whole incident probally scared me away from ubuntu for a while

You will regret it. Trust me, I sell Vista PC's every day and it is taking a toll on my patience.

You should try the Ubuntu Live CD in the future to test out Ubuntu without worrying about damaging anything. 700MB download, burn the ISO onto a disk using Nero, put it in the disk drive, restart the PC and off you go.

[http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)

Also considering that you're using Vista I'd assume you have decent specs, so that should help you run Ubuntu in the Live mode, which can be quite a lot slower than when it is fully installed.

Good luck with that one!

---

