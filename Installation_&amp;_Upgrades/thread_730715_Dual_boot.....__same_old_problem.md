---
title: "Dual boot.....  same old problem"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Pain Killer on 2008-03-21
Well i am new to ubuntu(and i don't know much about windows or computer either)........ :confused:

I have a problem i getting a dual boot.....

I have 2 hard disks ...i had windows XP in my first hard disk...After some time i installed ubuntu in my second hard disk....

But the Grub does not shows any option to boot windows...

_OUTPUT_  sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3650364f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9732    67930852+   f  W95 Ext'd (LBA)
/dev/sda5            1276        5099    30716248+   7  HPFS/NTFS
/dev/sda6            5100        9732    37214541    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe386e386

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    5  Extended
/dev/sdb5               1        6079    48829504+  83  Linux
/dev/sdb6            6080        6201      979933+  82  Linux swap / Solaris
/dev/sdb7            6202       18359    97659103+  83  Linux
/dev/sdb8           18360       30401    96727333+  83  Linux



**_menu.lst_**


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
timeout		0

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
# kopt=root=UUID=8ea6f668-cbeb-46a5-be1d-997bec23867e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8ea6f668-cbeb-46a5-be1d-997bec23867e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8ea6f668-cbeb-46a5-be1d-997bec23867e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I have windows installed in sda1..

plz help

---

### Post by sandysandy on 2008-03-21
u need to make an entry for windows in ur menu.lst file.

just search the forums.

enough threads are there on the subject.

regards

---

### Post by bobnutfield on 2008-03-21
Hello

Please note:

> # title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1

In this section of the menu.lst you provided is the entry for booting windows.

You will need to remove the # from each line and edit to root (hd0,0) to show which partition contains windows.  If windows is on your first hard disk and the first partition, then it is OK as is.

Hope this helps

Bob

---

### Post by forestpixie on 2008-03-21
Try this 
backup grub first
```
sudo cp  /boot/grub.menu.lst /boot/grub.menu.lst.bak
```

open to edit

```
gksudo gedit /boot/grub.menu.lst
```

go to end of file after the ### END DEBIAN AUTOMAGIC KERNELS LIST

add this and see what happens when you reboot, but there are hundreds of similar threads all you need to do is search.

> title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Pain Killer on 2008-03-22
I have searched many similar threads but can't get sol. of this new problem... :(

i added these lines in menu.lst

> title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

NTLDR[/B] missing..
Is my windows corrupted or i have selected wrong partition....

PLZ help

---

