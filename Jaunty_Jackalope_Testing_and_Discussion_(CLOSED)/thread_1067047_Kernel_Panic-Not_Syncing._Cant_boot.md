---
title: "Kernel Panic-Not Syncing. Cant boot"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by douham on 2009-02-11
Hi, trying to boot kernel 28-7 in normal or recovery mode results in
"kernel panic -not syncing : VFS: unable to mount foot fs on unknown block error." Can boot into the 28-6 kernel OK. I have checked all the grub entries and cant find any errors but will defer to the experts and incl. my menu.lst.
The machine was running like a pig, last session in 28-7 with an unknown program trying to prevent shutdown, same prob also in 28-6.
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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=UUID=3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-7-generic
uuid		3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d
kernel		/boot/vmlinuz-2.6.28-7-generic root=UUID=3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-7-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-7-generic (recovery mode)
uuid		3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d
kernel		/boot/vmlinuz-2.6.28-7-generic root=UUID=3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d ro  single
initrd		/boot/initrd.img-2.6.28-7-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-6-generic
uuid		3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d
kernel		/boot/vmlinuz-2.6.28-6-generic root=UUID=3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-6-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-6-generic (recovery mode)
uuid		3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d
kernel		/boot/vmlinuz-2.6.28-6-generic root=UUID=3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d ro  single
initrd		/boot/initrd.img-2.6.28-6-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		3fb5f466-8dc2-4d7d-9972-ad0b6db6b40d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=39c732e9-f292-44bd-9c86-8a0bfe69cc6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=39c732e9-f292-44bd-9c86-8a0bfe69cc6f ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=39c732e9-f292-44bd-9c86-8a0bfe69cc6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=39c732e9-f292-44bd-9c86-8a0bfe69cc6f ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=39c732e9-f292-44bd-9c86-8a0bfe69cc6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=39c732e9-f292-44bd-9c86-8a0bfe69cc6f ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

---

### Post by pressureman on 2009-02-11
I have a feeling that 2.6.28-7 is causing me the occasional hard lockup too. It's happened three or four times since installing it, but since the machine freezes, it's kinda hard to definitively point the finger.

---

### Post by douham on 2009-02-11
Pressureman, I had the occasional lockup also. I'm not sure if I run an update grub with the alpha 4 cd will fix the problem.

---

