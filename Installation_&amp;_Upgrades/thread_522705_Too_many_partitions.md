---
title: "Too many partitions"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by japycz on 2007-08-10
Is there a way to have just xp and one ubuntu simultanously? 

It seems that I have created too many partitions for ubuntu and when opening boot screen I have an option to choose xp or 8 ubuntu's? I think that experimenting did not do me any good. How can I start clean? I understand that if I choose entire disk space it will only install ubuntu. Does that mean that it will remove xp? If so, how can I avoid that?

Japycz

---

### Post by logos34 on 2007-08-10
Not sure what you did but it sounds like Grub menu screen is merely showing the different kernels + recovery modes + memdisk options available to you--they're all on root partition (it's not like you have 8 linux partitions--at least I don't think so!) Maybe you upraded?  

Try just commenting the older ones out with a '#" at the beginning of each line in menu.lst.  They won't show up then.  Or delete/uninstall the older kernels in /boot.

---

### Post by japycz on 2007-08-10
I think this is the problem. Can you please be more specific about using "commenting the older ones out with a '#" at the beginning of each line in menu.lst" and "Or delete/uninstall the older kernels in /boot." I am from the generation that does not quite take the computing for granted. Another words I struggle to understand a lot of replays.

Regards,

Japycz

---

### Post by logos34 on 2007-08-10
Like this:

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot


Could you post your men.lst and fdisk output so I we can better see what's going on?
[B]
sudo fdisk -l[/B] (that's a lowercase L)
[B]
cat /boot/grub/menu.lst[/B]

---

### Post by japycz on 2007-08-11
Here we go:
stan@stan-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bfb12d00-c7d2-4966-af2e-d5b9d9f5de17 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bfb12d00-c7d2-4966-af2e-d5b9d9f5de17 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bfb12d00-c7d2-4966-af2e-d5b9d9f5de17 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bfb12d00-c7d2-4966-af2e-d5b9d9f5de17 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bfb12d00-c7d2-4966-af2e-d5b9d9f5de17 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d6796bbd-57a1-4f29-9fa4-7275f2a426f9 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d6796bbd-57a1-4f29-9fa4-7275f2a426f9 ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d6796bbd-57a1-4f29-9fa4-7275f2a426f9 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d6796bbd-57a1-4f29-9fa4-7275f2a426f9 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu, memtest86+ (on /dev/sda2)
root            (hd0,1)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title           Ubuntu 7.04 (7.04) (on /dev/sda4)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda4 
savedefault
boot

stan@stan-desktop:~$

---

### Post by japycz on 2007-08-11
Hello,

For same reason when typing sudo fdisk -l, I am not able to type my password. ???

Japycz

---

### Post by logos34 on 2007-08-11
just hit enter after you type password (it goes in invisible)

---

### Post by CowzRule on 2007-08-11
Try this. In the Terminal put```
gksudo gedit /boot/grub/menu.lst
```Look for the following section> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
Change the last line> # howmany=allto> # howmany=1Save and close. Now, in the terminal put```
sudo update-grub
```Now when you reboot it will only show the newest kernel.

---

### Post by logos34 on 2007-08-11
Looks like you have 3 linux root partitions--sda2,4,7.  You're on sda7 (hd0,6)--at least that's the default. You could eliminate the other (redundant) partitions without affecting windows on sda1.  But I'll have to see your fdisk.

---

