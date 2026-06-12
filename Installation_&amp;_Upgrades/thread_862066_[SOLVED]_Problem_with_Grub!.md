---
title: "[SOLVED] Problem with Grub!"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by libe on 2008-07-17
Let me give you the background of my problem,
I partitioned my hard disk (sata) with GParted (1 ntfs partition,1 ext3 and 1 swap) after a low-level format and installed (s)Vista but i regretted it from the beginning and decided to move on Ubuntu 8.04 and so i did but here comes my problem,during the boot up process i can't access the usual grub menu where you can select which os you want to boot.
I tried startup-manager and increased the timeout in bootloader menu to 30 seconds but with no result since it still boots in Vista and gives no options to select!
What are my options,can i fix it and bring back the grub menu?
Right now i can start in Ubuntu only by booting from livecd and selecting the last option "boot from the first hard drive"!

---

### Post by scragar on 2008-07-17
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

basicaly you need to restore grub by the sounds of it vista has overwriten it with it's mbr.

---

### Post by logos34 on 2008-07-17
no, if vista had overwritten grub even the live cd opyion 'boot frm first hdd' couldn't get you into ubuntu.  

You have just one hard disk?

Post your menu.lst

gksudo gedit /boot/grub/menu.lst

---

### Post by libe on 2008-07-17
Is it clear that i installed vista first and then Ubuntu?
Is it possible that vista has overwritten grub since it's been installed first?
Or during the partitioning with GParted it installed grub simultaneously(stupid question?)?

> **logos34 said:**
> no, if vista had overwritten grub even the live cd opyion 'boot frm first hdd' couldn't get you into ubuntu.  

You have just one hard disk?

Post your menu.lst

gksudo gedit /boot/grub/menu.lst

I have 4 sata drives.
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
timeout		32

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
# kopt=root=UUID=8418cc3a-196d-4078-9ef5-94d477fe7fd0 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8418cc3a-196d-4078-9ef5-94d477fe7fd0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8418cc3a-196d-4078-9ef5-94d477fe7fd0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8418cc3a-196d-4078-9ef5-94d477fe7fd0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8418cc3a-196d-4078-9ef5-94d477fe7fd0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb4
title		Windows Vista/Longhorn (loader)
root		(hd1,3)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by libe on 2008-07-17
So what do you think?

---

### Post by logos34 on 2008-07-17
> **libe said:**
> Is it clear that i installed vista first and then Ubuntu?
Is it possible that vista has overwritten grub since it's been installed first?

yes it's clear...I was speaking more hypothetically, but in your case it couldn't have simply because you installed it before linux.  (and it's not even remotely possible that vista could have overwritten the mbr after the fact, totally on its own)

> Or during the partitioning with GParted it installed grub simultaneously(stupid question?)?

no, not a chance

>  I have 4 sata drives.

bingo.  there's the culprit. I thought you might have more than one hard disk.

According to menu.lst the vista/ubuntu disk is /dev/sdb... I think that's the actual boot drive with the vista bootloader on the MBR.  But grub appears to be scanning the sata channels rather than the actual bios hard disk boot priority, and might have put grub on /dev/sda.  So go into the Bios and change the hard disk boot priority so sda is first and sdb is second.

Post back with results.

---

### Post by libe on 2008-07-17
Thx a lot guys for the help!
logos34 thx a lot it worked!

---

### Post by logos34 on 2008-07-17
Glad to hear it worked without further ado.  

enjoy ubuntu!

---

