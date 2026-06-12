---
title: "Is It Safe ?"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by james_bandido on 2008-05-29
i have downloaded the alternate CD to upgrade my 7.10 to 8.04 since my internet connection is slow.

when i had finished the upgrade, it seems my grub/menu was messed up.

this is now my menu.lst

```

title        Ubuntu 8.04, kernel 2.6.24-17-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro splash vga=792
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro single
initrd        /boot/initrd.img-2.6.24-17-generic

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro splash vga=792
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, kernel 2.6.22-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro splash vga=792
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional Service Pack 3
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```i dont know what went wrong or what but everything seems to be working fine though.

my question is this, is it safe to delete the following entries ?

```

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro splash vga=792
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, kernel 2.6.22-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro splash vga=792
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

```can someone also explain why this happened to my grub ? 

thanks very much in advance.

---

### Post by barnex on 2008-05-29
I don't think there's anything wrong with that. After every upgrade, Ubuntu keeps your previous kernels to allow you boot into them in case of problems. My list is a bit shorter because I did a clean install of 8.04, but still, the previous kernel is in grub too.

So I wouldn't worry ;)

---

### Post by james_bandido on 2008-05-29
thank you very much ... 

i think i'll keep a backup copy just in case ... 

and edit my grub to a shorter one ... 

thanks !!!

---

### Post by hyperair on 2008-05-29
You're missing your top few lines of your menu.lst. Copy the following and place it before the code you've posted:
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
#default         4

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
# kopt=root=UUID=1e31cd41-b817-4f95-a1f5-8216f78447b2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=splash vga=792

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
# howmany=4

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

```

Then run ```

sudo update-grub

```

Everything should work fine after that.

---

### Post by james_bandido on 2008-05-29
@hyperair, thanks very much, i almost forgot that topmost part of the menu.lst

---

### Post by zvacet on 2008-05-29
Another option is to delete 2.6.22-14 kernel in synaptic.Look for **linux-image** package and that select 2.6.22-14 and delete it.That way you will get little bit of free space and remove things you don´t need anymore.

---

