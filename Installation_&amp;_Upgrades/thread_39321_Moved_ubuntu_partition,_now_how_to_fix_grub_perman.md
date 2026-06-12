---
title: "Moved ubuntu partition, now how to fix grub permanently?"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by Dogmeat on 2005-06-04
I moved my ubuntu partition to my newer hard drive, as the other one was slowly going nuts. I changed the root in menu.lst, but I noticed I get an error 15 file not found when grub tries to run savedefault, why is this? Also I installed an optimized kernel and ubuntu changed every entry in the menu.lst to my old instalation partition, and I had to fix it again. 

I can boot fine now without savedefault, but it would be nice to put it back there (it must do something important or it wouldn't be on the default instalation)

I'd like to let ubuntu know "officially" where it's new home is  :razz: 

What should I edit to fix these two problems?

---

### Post by spd106 on 2005-06-04
Hi, it would be useful if you can post the /boot/grub/menu.lst. 

Check that you have the line "default saved" somewhere before the options and the line "savedefault" before "boot" in the option you want.

This webpage might be useful.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Good luck

---

### Post by Dogmeat on 2005-06-05
Here's my menu.lst:

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
splashimage (hd0,1)/boot/grub/images/usplash.xpm

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdd1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.10-5-686
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1
``` 

Note that I removed savedefault before every boot, because if I put it there grub doesn't boot (says Error 15: file not found)

That's just a minor nuisance, because I want it to boot the first (686) menu entry by default all the time.

The problem is, if I install a new kernel (like the optimized one I got) with apt-get, menu.lst gets automagically edited, and it changes EVERY ENTRY to the old partition in the old hard drive and thats what I want to change, instead of having to edit every menu.lst entry again whenever ubuntu changes this file.

---

### Post by Dogmeat on 2005-06-09
well I deleted some files in boot and now grub-install generates menu.lst correctly. However I still don't understand why I have to manually remove every "savedefault" entry, because if they are there I get a Error 15: File not found error every boot! Why am I getting this error? It used to work in the other partition!

---

