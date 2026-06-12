---
title: "Dual boot with XP - but only boots into Ubuntu!"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by LHMike on 2008-06-23
Hi all,
I installed Ubuntu on a partition I created on my 60Gb hard drive, after the windows XP partition, and I'm quite impressed with everything it does. After a couple of days playing, however, I have realised I have no way of booting in XP as GRUB doesn't give it to me in the list of options at startup.

It is probably also worth noting that actually creating the Linux partition was a right pain, as GParted wouldn't (and still doesn't) read properly from the NTFS XP partition. I had to use Partition Logic to resize and create the partitions. 

The Ubuntu partition is experimental and expendable - the XP partition is ultimately expendable but I wouldn't mind being able to get back at it. 

Cheers for any help,

Mike


N.B. Running sudo fdisk -l gives:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe944be2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5610    45062293+   7  HPFS/NTFS
/dev/sda2            5611        7165    12490537+  83  Linux
/dev/sda3            7166        7296     1052257+  82  Linux swap / Solaris
```

boot/grub/Menu.lst contains:

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
timeout		25

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
# kopt=root=UUID=f94d2618-4291-4865-adea-43869cabf3ee ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f94d2618-4291-4865-adea-43869cabf3ee ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f94d2618-4291-4865-adea-43869cabf3ee ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f94d2618-4291-4865-adea-43869cabf3ee ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f94d2618-4291-4865-adea-43869cabf3ee ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Pumalite on 2008-06-23
Edit menu.lst Add below Debian Automagic Line:

title Windows XP 
root  (hd0,0)
makeactive
savedefault
chainloader + 1

---

### Post by LHMike on 2008-06-23
Thanks for the quick reply :-)

I did that, and Windows XP appeared in the list, but GRUB gave me "Error 1: Filename must be either an absolute pathname or blocklist" when choosing the XP option.

I tried the method that seemed to work [in this thread]("http://ubuntuforums.org/showthread.php?t=372070"), i.e. removing the savedefault line, but that still threw up the same message.

Eurgh...

---

### Post by Pumalite on 2008-06-23
Remove 'makeactive' and see what happens.

---

### Post by LHMike on 2008-06-23
Ok, I gave that a go but the same error appears when I try to boot into XP. I think I'm prepared to sacrifice Ubuntu now for the moment - seems to be giving me a lot of hassle - is there a way to completely remove it, leaving me with XP only? Will the computer then boot into XP?

Cheers.

---

### Post by meierfra. on 2008-06-23
> chainloader + 1

This is the culprit. It needs to be

> chainloader +1
(no space between "+" and "1")

---

### Post by Pumalite on 2008-06-23
Thanks meierfra; my bad.

---

