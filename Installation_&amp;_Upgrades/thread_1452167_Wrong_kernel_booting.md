---
title: "Wrong kernel booting"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by gleble on 2010-04-11
Grub use to open an old kernel I tried to edit /boot/grub/menu.lst to open the one I wanted. Th edit gets saved but it still opens in the wrong kernel. i.e when edit menu.lst it has no effect. I have tried running sudo grub-update. I've read piles of forum entries to no avail. I am running Jaunty.

---

### Post by ajgreeny on 2010-04-11
Simply install startup-manager, and use that to set things right.

Or post the output of cat /boot/grub/menu.lst and tell us in more detail which kernel is booting and which one you want.  This latter method may end up  making you more informed about grub, but it will not help much longer as grub2 is now installed by default, and that has no menu.lst file, and is configured in a very different manner.

---

### Post by phillw on 2010-04-11
Hi,
just to keep things clear, would you post the result of ```
grub-install -v
```

I'd just like to ensure you're still running grub legacy and have not upgraded to grub(2)

grub-install (GNU GRUB 1.xx.......) means you are 'new' grub (aka grub2); grub-install (GNU GRUB 0.xx.......) means grub legacy. 

Regards,

Phill.

---

### Post by gleble on 2010-04-12
The output of sudo grub-install -v is grub-install (GNU GRUB 0.97)
So I think I am using the right grub

cat /boot/grub/menu.lst gives
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

default		8

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=856d304d-903a-4c0d-83fc-b7585c43c09e

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
# defoptions=splash

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
# savedefault=true

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-9-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.27-9-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 9.04, kernel 2.6.24-22-generic
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=856d304d-903a-4c0d-83fc-b7585c43c09e ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 9.04, memtest86+
uuid		856d304d-903a-4c0d-83fc-b7585c43c09e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,2)
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
```

I am trying to start Ubuntu 9.04, kernel 2.6.28-13-generic but it always comes up with Ubuntu 9.04, kernel 2.6.27-11-generic

I have installed startupmanaager. I ran it and set it to Ubuntu 9.04, kernel 2.6.28-13-generic  Restarted and it still doesn't work.

Output of startupmanager

```
Grub2 not detected
Version: ImageMagick 6.5.3-10 2009-08-10 Q16 OpenMP http://www.imagemagick.org
Copyright: Copyright (C) 1999-2009 ImageMagick Studio LLC

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash detected
Splashy not detected
```

I've attached a screenshot of startupmanager

---

### Post by ajgreeny on 2010-04-12
If I were you I would let the system boot to the most recent kernel, ie 2.6.28-18.  Is there some reason why you don't want that one?

If for some reason that you can't solve, that latest version will not boot to a successful, stable system, just uninstall it in synaptic and leave the kernels that will boot successfully.  There is no point having space wasted by kernels that you can't use.  You can certainly uninstall all the 2.6.27-x versions, which came from a previous ubuntu version if I remember correctly, then they will not be able to boot at all.

---

### Post by gleble on 2010-04-13
This gets stranger. I've deleted 2.6.27-11-generic form menu.lst but it still gets shown in the initial grub screen whereas  2.6.28-18-generic appears in menu.lst but not the initial grub screen. Its like I'm looking at the wrong file but how can I be?

---

### Post by ajgreeny on 2010-04-13
You don't happen to have more than one linux install on your hard disk do you, with the menu.lst from grub being generated by a linux that you are not booting to?  This could explain why removal of a kernel is not removing it from grub's menu.

Just to help out the confusion a bit, can you post the output of ```
sudo fdisk -l
sudo blkid
``` which will show all the partitions you have, and then all the UUIDs of those partitions.  It may clarify things a bit.

Then again, it may not.  Worth a look, however.

---

### Post by gleble on 2010-04-15
Dammit you're right, there's an old version of Intrepid on there. All sorted now. Cheers

---

