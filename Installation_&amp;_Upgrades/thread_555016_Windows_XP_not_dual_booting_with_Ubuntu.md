---
title: "Windows XP not dual booting with Ubuntu"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by darthlunchbox42 on 2007-09-19
I've encountered a seemingly common problem with GRUB.  I have Windows XP installed on my computer, on a 250GB SATA drive, and I recently installed Ubuntu 7.04 onto the same hard drive on a partition I created during installation.  Now, I can't get Windows to boot from GRUB, it just hangs with 'Starting Up...' displayed.

This is my menu.lst:
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
# kopt=root=UUID=a320d560-8c42-44f3-b1f9-dae3dfb78441 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a320d560-8c42-44f3-b1f9-dae3dfb78441 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a320d560-8c42-44f3-b1f9-dae3dfb78441 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a320d560-8c42-44f3-b1f9-dae3dfb78441 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a320d560-8c42-44f3-b1f9-dae3dfb78441 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I've tried to changing 'root' to 'rootnoverify' without success.  I would include fdisk in the post, but  when I put in the following code, it just says that gedit could not detect the character coding.

```
 gksudo gedit /sbin/fdisk -l
```

I am quite new at Linux, so if someone could help we with this step by step, that would be greatly appreciated.  Thanks!

---

### Post by logos34 on 2007-09-19
it's

sudo fdisk -l

Maybe the boot flag is on the wrong partition or you need to run chkdsk.

---

### Post by darthlunchbox42 on 2007-09-19
Alrighty, here's fdisk:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18972   152392558+   7  HPFS/NTFS
/dev/sda2   *       18973       30023    88767157+  83  Linux
/dev/sda3           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

```

And, logos, this is just me being a super n00b, but I'm not entirely sure what you said.  :confused:

---

### Post by logos34 on 2007-09-19
yep, you need to change the boot flag (*) to windows/sda1. you can use gparted to do it.  hopefully that will do the trick.

'chkdsk': I was referring to checkdisk (maybe it won't be necessary if it's a boot flag issue)

[B]sudo apt-get update
sudo apt-get install gparted[/B]

**sudo gparted**
right-click sda2>manage flags>untick 'boot' box

then tick the boot box on sda1

---

### Post by darthlunchbox42 on 2007-09-20
Alright, I went in and switched the boot flag to sda1.  However, I tried to boot into Windows and it still didn't work.  Now, Ubuntu only displays in nothing higher than 640 by 480.  Yar...


When I look at the sda1 partition in gparted it has a warning saying that it is unable to read the contents of this filesystem.  Is this just because the partition is NTFS or something else?  It also does not display any numbers in the 'used' and 'unused' columns for the partition, only in the sda2 partition.

---

### Post by logos34 on 2007-09-20
You need to run a filesystem check.  Boot from the XP install cd, enter the recovery console, and run chkdisk with repair option:
[B]
chkdsk /r[/B]

I'm not sure why it borked your resolution.

---

### Post by mikexgough on 2007-09-21
[QUOTE= Now, I can't get Windows to boot from GRUB, it just hangs with 'Starting Up...' displayed."
This happened to me so I went back to windoze until I could find a work around...........

---

