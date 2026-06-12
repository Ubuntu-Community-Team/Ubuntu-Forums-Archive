---
title: "GRUB help"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by benjfield on 2008-05-10
I just installed 8.04 on my laptop, and it hasn't discovered my install of xp for GRUB. I tried to change the settings manually, but I've come across problems because for some reason XP is in an extended partition. If any ones got an easy way of fixing it I'd really appreciate it. When I use this option it gives me a disk read error.
My Grub option:

title		Windows XP
map 		(hd0,0) (hd0,5)
map 		(hd0,5) (hd0,0)
rootnoverify	(hd0,5)
chainloader	+1

fdisk -l printout:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe288fc9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       15855   117116928    6  FAT16
Partition 2 does not end on cylinder boundary.
/dev/sda3           15856       27790    95867887+   f  W95 Ext'd (LBA)
/dev/sda4           27791       30401    20972857+  83  Linux
/dev/sda5           15856       22569    53930173+   e  W95 FAT16 (LBA)
/dev/sda6           22570       27790    41937651    7  HPFS/NTFS

sda1 being a recovery partition i think,
sda2 being vista, though why its showing up as fat16 I'm not sure...
sda4 being 8.04
sda5 being empty,
sda6 being XP
and both sda5 and sda6 are part of sda3

Thanks in advance.

---

### Post by Pumalite on 2008-05-10
Post:
cat /boot/grub/menu.lst

---

### Post by benjfield on 2008-05-10
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
# kopt=root=UUID=9e3b4d09-98b4-47c1-87ac-ec5e34f57f37 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e3b4d09-98b4-47c1-87ac-ec5e34f57f37 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e3b4d09-98b4-47c1-87ac-ec5e34f57f37 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Windows XP
map 		(hd0,0) (hd0,5)
map 		(hd0,5) (hd0,0)
rootnoverify	(hd0,5)
chainloader	+1

---

### Post by Pumalite on 2008-05-10
Edit your menu.lst and remove all this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

title Windows XP
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
rootnoverify (hd0,5)
chainloader +1

Change the 'root' line of the remaining Windows entry to (hd0,1)
Save, exit and reboot.

---

