---
title: "Can't boot with kernels newer than 2.6.27-5"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by brazzmonkey on 2008-10-18
hello there,

i'm running intrepid 64-bit on a fakeraid array.
i cannot boot any kernel that's newer than 2.6.27-5 : i get something like
```
 ALERT! /dev/mapper/isw_decajbafgg_System7 does not exist. Dropping a shell.
- busybox stuff -
(initramfs)
```

i don't know what's going on, why i would get such an error with one kernel entry and not the other.

my grub menu.lst
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
# kopt=root=/dev/mapper/isw_decajbafgg_System7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash rootflags=data=writeback

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
# altoptions=(recovery mode) single rootflags=data=writeback

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_decajbafgg_System7 ro quiet splash rootflags=data=writeback 
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_decajbafgg_System7 ro  single rootflags=data=writeback
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-6-generic root=/dev/mapper/isw_decajbafgg_System7 ro quiet splash rootflags=data=writeback 
initrd		/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-6-generic root=/dev/mapper/isw_decajbafgg_System7 ro  single rootflags=data=writeback
initrd		/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-5-generic root=/dev/mapper/isw_decajbafgg_System7 ro quiet splash rootflags=data=writeback 
initrd		/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-5-generic root=/dev/mapper/isw_decajbafgg_System7 ro  single rootflags=data=writeback
initrd		/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-4-generic root=/dev/mapper/isw_decajbafgg_System7 ro quiet splash rootflags=data=writeback 
initrd		/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-4-generic root=/dev/mapper/isw_decajbafgg_System7 ro  single rootflags=data=writeback
initrd		/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,4)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```
any guidance is appreciated.

thanks

---

### Post by nanog on 2008-10-18
/dev/mapper maps your fake raid array. assuming that there is not something wrong with your raid you need to file a kernel bug.

---

### Post by brazzmonkey on 2008-10-19
it works fine with 2.6.27-5...
i'll file a bug.

---

### Post by brazzmonkey on 2008-10-19
i found this 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269411](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269411)
which may (or may not..) be related to my issue.

---

### Post by brazzmonkey on 2008-10-24
ubuntu has gone RC, and there doesn't seem to be much activity on this bug. i'm afraid it'll still be present in final...

---

