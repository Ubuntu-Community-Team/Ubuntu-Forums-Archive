---
title: "linux 2.6.27-5 system won't boot"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wilbur.harvey on 2008-10-06
Last night, after upgrading to the latest 2.6.27-5 kernel, my system won't boot. I could still boot with the old kernel. Some kind of VFS can't read block at (0,0) error.

---

### Post by bobnutfield on 2008-10-06
This error is telling you that the kernel is not being found or is incomplete.  The complete message is probably telling you to append the root=" " label in your grub menu. It could also be a corrupt initrd. It could have been an incomplete download and install.  If you can still boot into a previous kernel, boot into it and post the /boot/grub/menu.lst file.

---

### Post by wilbur.harvey on 2008-10-07
Here is the contents of my /boot/grub/menu.lst file

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
# hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel Default
root		(hd0,0)
kernel		/boot/vmlinuz root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro quiet splash 
quiet

title		Ubuntu intrepid (development branch), kernel Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro  single

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro quiet splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-5-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro  single
initrd		/boot/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=41d5223d-7c9b-477c-9fc8-82633c03ff3f ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by wilbur.harvey on 2008-10-07
I tried re-installing 2.6.27-5 kernel.

The exact error message is:

0.800175 Kernel Panic not syncing: VFS: Unable to mount root fs on unknown block (0,0)

This is a machine with a boot drive, and a soft raid0 which is bind mounted to /home.

2.6.27-4 boots and runs fine.

wharvey@hnlwnh1:~/Desktop$ uname -a
Linux hnlwnh1 2.6.27-4-generic #1 SMP Wed Sep 24 01:29:06 UTC 2008 x86_64 GNU/Linux
wharvey@hnlwnh1:~/Desktop$

---

### Post by der_hede on 2008-10-07
The two entries labeled "Ubuntu intrepid (development branch), kernel Default" seem uncommon to me.

Did you tried to boot the "kernel 2.6.27-5-generic" entry? Does "kernel 2.6.27-4-generic" work or only "kernel Last successful boot"?

Which of those files do exist:
```
/boot/vmlinuz
/boot/vmlinuz-2.6.27-5-generic
/boot/initrd.img-2.6.27-5-generic
/boot/vmlinuz-2.6.27-4-generic
/boot/initrd.img-2.6.27-4-generic
```

---

