---
title: "Do I need the 2.6.24.16 kernel when I have the2.6.24.17 ?"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Sathors on 2008-06-02
So I was just reading my /boot/grub/menu.lst, and I've noticed that I have two different loaders. I past you all the file

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
# kopt=root=UUID=27a144bd-6eb9-47d6-b4e3-c5edc5fbe98d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

gfxmenu (hd0,6)/boot/grub/message.dark_ubuntu

## ## End Default Options ##


title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=27a144bd-6eb9-47d6-b4e3-c5edc5fbe98d ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=27a144bd-6eb9-47d6-b4e3-c5edc5fbe98d ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=27a144bd-6eb9-47d6-b4e3-c5edc5fbe98d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=27a144bd-6eb9-47d6-b4e3-c5edc5fbe98d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1


So I was just wondering why is there 2 different ubuntu loaders, can I remove the older one of the grub (it takes place in the list), and if I can remove all the 2.6.24.16 of my computer ?

What are the differencies between those two ?
Is it just a preventive measure in case of a crash ?

Thanks for your answers, I have resaearched it butr found nothing, not knowing clearly what it was.

Good Night

---

### Post by Pumalite on 2008-06-02
It's good to have something to boot in case your working kernel fails. Leave it as it is.

---

### Post by Sathors on 2008-06-02
As you've seen I'm multibooting with vista so I can access it if I need to.
No precisions ?

Thanks

---

### Post by Pumalite on 2008-06-02
You seem to be doing fine; unless you ask me a specific question.

---

### Post by Sathors on 2008-06-04
> 

So I was just wondering why is there 2 different ubuntu loaders, can I remove the older one of the grub (it takes place in the list), and if I can remove all the 2.6.24.16 of my computer ?

What are the differencies between those two ?
Is it just a preventive measure in case of a crash ?

Thanks for your answers, I have resaearched it butr found nothing, not knowing clearly what it was.

Good Night

The questions are just above ^^

---

### Post by endz on 2008-06-04
how bout have kernel 2.6.24.18?
should i remove 2.6.24.16?

---

### Post by conscious on 2008-06-04
Yes, you can remove old kernels. It should not cause any troubles if the current one is working fine. You can uninstall kernels using Synaptic, just look for installed packages starting with "linux" and containing "2.6.24-16" or "2.6.24-17" (whichever you want), then remove them. The grub menu will be updated automatically.

---

### Post by endz on 2008-06-04
EDIT:*sorry mistype*
btw thx for the answer

---

### Post by OpposingForce on 2008-06-04
Yeah I just upgraded to 18 and removed the 16 (I still have 17 as a backup just in case)

---

### Post by Pumalite on 2008-06-04
Sure. Make sure 17 and 18 are working well first.

---

### Post by housam on 2008-06-04
I think that you must have at least one kernel as a reserve . just in case you may need it.

---

