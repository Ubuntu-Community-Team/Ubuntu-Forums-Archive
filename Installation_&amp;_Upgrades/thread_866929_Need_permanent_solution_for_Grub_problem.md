---
title: "Need permanent solution for Grub problem"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by miracleman on 2008-07-22
Hi,

I have Ubuntu 8.04 installed dual-booting with XP. Installation went without a hitch but after some reboots, I am faced with endless rebooting when the grub menu is loading. 

After searching for a solution, I saw this thread:

[http://ubuntuforums.org/archive/index.php/t-625562.html](http://ubuntuforums.org/archive/index.php/t-625562.html)

So basically what I did was:

1. Boot with the live cd and selected "Try Ubuntu without making any changes to your computer"

2. In terminal: 
[I]sudo update-grub
sudo grub[/I]


At the "grub>" prompt:
[I]find /boot/grub/menu.lst
root (hd0,2)
setup (hd0)
quit[/I]

It works! My computer can boot normally. But the problem resurfaces every few reboots. 

Can anyone guide me as to how I can make the above solution permanent?

Much appreciated!

---

### Post by Pumalite on 2008-07-22
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by miracleman on 2008-07-22
> **Pumalite said:**
> Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

Thanks for your quick reply!

**sudo fdisk -lu**
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3a6552e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    14338047     7168000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    14338092   277387151   131524530    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       277387152   310627355    16620102   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4       310627356   312580415      976530   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS


**cat /boot/grub/menu.lst**
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
# kopt=root=UUID=0ee39e0b-1ec0-42d1-9d7e-c444ebc89f10 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ee39e0b-1ec0-42d1-9d7e-c444ebc89f10 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ee39e0b-1ec0-42d1-9d7e-c444ebc89f10 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
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
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Pumalite on 2008-07-22
This:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
Should be below the automagic kernel line and should be:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
root (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
If you don't heve Vista; remove the enthy from menu.lst. Beyond that; you seem to have a Partition Table problem in your first drive.
Use rescuecd to check it and fix it if necessary:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Burn to disk and boot from it.
savedefault
makeactive
chainloader +1

---

### Post by miracleman on 2008-07-22
Thanks Pumalite!

I put Windows XP on top of the list because I want it to load by default. Did I do it wrong? What's the correct way to do it?

I will remove it and remove the vista thingy as well. I'm using a laptop and that's the recovery partition.

Thanks very much for helping out. Its great that this community is so supportive.

---

### Post by Pumalite on 2008-07-22
To make Vista default; edit menu.lst and change 'default=0' to 'default=?', ? being the number that Vista is on the list minus 1 ( Grub starts counting from 0)

---

### Post by miracleman on 2008-07-22
> **miracleman said:**
> Thanks Pumalite!

I put Windows XP on top of the list because I want it to load by default. Did I do it wrong? What's the correct way to do it?

I will remove it and remove the vista thingy as well. I'm using a laptop and that's the recovery partition.

Thanks very much for helping out. Its great that this community is so supportive.

umm Pumalite, pls disregard the quoted post. I already figured out how to do it, just change "default" to the item number in grub.

thanks for your help, I hope this permanently solves my problem!

---

### Post by Pumalite on 2008-07-22
Good luck!

---

