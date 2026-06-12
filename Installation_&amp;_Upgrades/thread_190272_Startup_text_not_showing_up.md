---
title: "Startup text not showing up"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Zillator on 2006-06-06
I've recently upgraded from Breezy to Dapper and now I don't see any startup or shutdown text. 

My friend was trying to spice up my Breezy installation by changing the startup text color, so I suspect this is the root of the problem, however I'm not able to find a fix for this myself as I don't know what exactly he modified. I can't ask him for help either, since he lives in a different city and I won't see him for a few weeks.

I hate having a blank screen all the time the computer is booting or shutting down, because I like to know what is going on and what exactly happened if something goes wrong. 

Can anybody point me in the right direction please?

---

### Post by rwabel on 2006-06-06
Same happened to me while installing dapper server edition. after a successfully installation nothing happens, even no grub appears.
Changing the monitor cable helped. very strange.

---

### Post by Zillator on 2006-06-08
[QUOTE=rwabel]Same happened to me while installing dapper server edition. after a successfully installation nothing happens, even no grub appears.
Changing the monitor cable helped. very strange.[/QUOTE]
This can't be my case, because I have a notebook :)
Also the grub works fine, I just don't see anything after choosing a boot option in the grub - not until I get to the desktop :-o

---

### Post by motoperpetuo on 2008-03-08
I've got the same thing. I don't see anything between when I choose my GRUB boot option and when the login page loads. That is, in normal mode. If I choose recovery mode, I see text. If anyone has a solution, please let us know.

---

### Post by dasunst3r on 2008-03-08
I suspect that it has to do with usplash not working properly.  When I want to see startup text, I hit Ctrl+Alt+F1 and then Ctrl+Alt+F8.  You could also check your boot parameters in /boot/grub/menu.lst.  Mine looks like this:

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
# kopt=root=UUID=4259f8c7-4410-4237-bfc3-feb1d2be2f42 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4259f8c7-4410-4237-bfc3-feb1d2be2f42 ro quiet **splash**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4259f8c7-4410-4237-bfc3-feb1d2be2f42 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Find a similar entry on your menu.lst and take out "splash" and see what happens.

---

