---
title: "Feisty Installation Problem"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by MamoruC on 2007-05-17
I have just tried installing Feisty from the LiveCD twice.  The first time, when I tried rebooting, the system would just sit there for a while before giving me this message
d3> ALERT! /dev/disk/by-uuid/xxxxxxxxx [can't remember all the numbers and such] does not exist.  Dropping to a shell!
Then it drops to Busybox.  The second time I tried installing, it started to load and just kicked out to busybox without giving me any error message.  The HD I'm trying to install to is a 40GB  Western Digital IDE.

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=afb4e7f7-f734-4e13-ab0f-dd4bfd38ccab /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=fbc79ee6-f93b-4dd2-9d06-32b4d701d3bc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

And here's my menu.list:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

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
# kopt=root=UUID=afb4e7f7-f734-4e13-ab0f-dd4bfd38ccab ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=afb4e7f7-f734-4e13-ab0f-dd4bfd38ccab ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=afb4e7f7-f734-4e13-ab0f-dd4bfd38ccab ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Can anybody help me with this?

---

### Post by dkulchenko on 2007-05-17
Exact same problem!! Hope someone knows a solution.

---

### Post by MamoruC on 2007-05-18
I just realized that Feisty didn't create any of the device files for my HD nor did it create the /dev/disk/by-uuid/ directory.

---

### Post by MamoruC on 2007-05-21
So nobody has any idea how to fix this?

---

### Post by dannyboy79 on 2007-05-21
can you simply change your menu.lst and your fstab so that it uses the /dev/hdxy or /dev/sdxy instead of the UUID's? just erase the uuid's from your fstab and make it so the line begins with the /dev/ instead. and for the menu.lst, make sure it says, /dev/hda1 instead of what it says now. Let me know if that does it. otherwise, did you check the md5sum of the iso after you downloaded it???? It sounds like if your device's aren't being created under /dev/ then you must have got a bad download.

---

### Post by MamoruC on 2007-05-21
I don't know.  I checked the CD before I installed and it said the CD was fine.

---

### Post by jerrylamos on 2007-05-21
There are some things to try in my post "Workarounds" on "Installation & Upgrades".  Oddly, I found putting my CD drives on IDE1 and the hard drives on IDE2 and then installing worked for me.  I've found the UUID stuff to be a holy mess so you could try deleting it carefully from /etc/fstab.  Make sure the mount point / is still there.

Looking at the SCSI code simulation of IDE, SATA, CD, Floppy, USB, and gosh knows what else, it seems to take a while (!) to get everything recognized and mounted.  In the meanwhile, to speed up Boot, some other things may have started that depend on the SCSI code being finished and it hasn't yet.  I'm no developer, but there seem to be a number of things like this with Feisty, I gather a lot of them came when some Debian scripts were put into Feisty on about Feb 10.

---

