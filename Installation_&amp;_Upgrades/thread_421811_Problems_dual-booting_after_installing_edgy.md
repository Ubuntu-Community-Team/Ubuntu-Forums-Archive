---
title: "Problems dual-booting after installing edgy"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Ekeluo on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/109702](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/109702) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I upgraded today to Fiesty Fawn from Edgy Eft (took me 2 days to download the needed 1050mb). Anyway after that grub refused to accept that I have a valid windows installation on /dev/hda1. It says "Error 12 - device specified not valid" or something along those lines. I have tried installing lilo but it says something is wrong with my fstab. Here's my complete menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9d587394-49e7-4fff-bbbe-5025563a8ff6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
makeactive
chainloader +1

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=9d587394-49e7-4fff-bbbe-5025563a8ff6 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=9d587394-49e7-4fff-bbbe-5025563a8ff6 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Please any help will be appreciated, need to solve this by 2moro morning (it's 22:00 here already). HELP!
Also if I rewrite the mbr with windows XP recovery tool from the CD, how do I re-add Ubuntu to the boot menu?

---

### Post by Ekeluo on 2007-04-29
Well well well will you look at that. I figured out the problem on my own after waiting for so long. Almost got my a** fried! Anyway I fixed it by specifying (hd0,0) instead of (hd0,1). Someone fix this!

---

### Post by undecidable on 2007-04-29
Note that your windows boot entry:
--# on /dev/sda1
--title Microsoft Windows XP Professional
--rootnoverify (hd0,1)
--makeactive
--chainloader +1

needs to be AFTER:
### END DEBIAN AUTOMAGIC KERNELS LIST

so that it doesn't get messed with during the upgrade,
(which will use parameters above
## ## End Default Options ##
to update everythng before 
### END DEBIAN AUTOMAGIC KERNELS LIST)

This might have caused your problem
in the first place,
which you then had to manually correct.

---

