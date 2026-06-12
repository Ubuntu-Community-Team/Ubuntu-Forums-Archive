---
title: "editing grub for vmalloc"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by kolibri on 2010-07-26
I want to edit a grub file, but none of the online instructions exactly match my files.

I'm trying to follow the instructions to add vmalloc=256M to a grub file, from here:


[http://ubuntuforums.org/showthread.php?t=1002287&page=2](http://ubuntuforums.org/showthread.php?t=1002287&page=2)
post 17

or

[http://ubuntuforums.org/showthread.php?t=1009612](http://ubuntuforums.org/showthread.php?t=1009612)
post 10

but my menu.lst file doesn't have the same wording.

This is what my menu.lst file has:
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
# kopt=root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 10.04 LTS, kernel 2.6.27-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.27-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 10.04 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro  single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

where exactly should I put the vmalloc=256 to try to get my nvidia card working?

---

### Post by Bachstelze on 2010-07-26
```
# kopt=root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro
```

Change to

```
# kopt=root=UUID=0e0d90c1-73f1-421f-a79e-30cd51b1296c ro vmalloc=256M
```

Then run

```
sudo update-grub
```

But why are you still using GRUB .97?

---

### Post by abhinav.gaur13@gmail.com on 2012-02-16
@Bachstelze
But why should this work? The line is commented.

---

