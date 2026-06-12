---
title: "Strange dual-booting multi disk issue"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by dkulchenko on 2008-08-19
All right, here's the story:

I started out with an IDE, PATA disk of 40GB patitioned as follows:

28GB ext3 Ubuntu
9GB ntfs Windows XP
2GB swap

It was running fine, dual booting fine. Then I got a new 320GB SATA disk. I created a 280GB ext3 partition, copied all the files over, and installed GRUB. My new layout is:

/dev/sda - IDE PATA 40GB

25GB ext3 empty
15GB ntfs Windows XP (shifted over with parted)

/dev/sdb - SATA 320GB

280GB ext3 Ubuntu (copied over and GRUBbbed)
30GB unallocated
3GB swap

Since SATA is sdb, I installed grub as follows:

grub> root (hd1,0)
grub> setup (hd1)

The problem now is, at boot, SATA is hd0, as soon as it's past boot, it becomes hd1. I've tried doing:

grub> root (hd0,0)
grub> setup (hd1)

But this fails with not finding any files on hd0,0, because while booted, it's hd1,0. I can boot into my system, but I have to edit the prompt each time to hd0. How can I fix this?

device.map:
```
(hd0)	/dev/sda
(hd1)   /dev/sdb
```

menu.lst:
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
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=28613ad8-380f-456b-8f20-e543912a80e7 ro

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
# defoptions=quiet splash vga=791

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=28613ad8-380f-456b-8f20-e543912a80e7 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=28613ad8-380f-456b-8f20-e543912a80e7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

What should I change? 

Thanks in advance.

---

### Post by manishtech on 2008-08-20
I can give you a good idea but not sure whether it would work or not. I came to know that the BIOS searches for MBR on the hard disk which is connected to the master.

Exchange the positions of SATA and PATA and try to boot from SATA one.

---

### Post by falcon61102 on 2008-08-20
Have you tried using the map command in the GRUB.  Add the following to your menu.lst:
```

map (hd0) (hd1)
map (hd1) (hd0)

```

That command allows you to boot up the second HD and it "thinks" it's the first HD.  This is normally for non-linux installs but it may work in your case.

---

