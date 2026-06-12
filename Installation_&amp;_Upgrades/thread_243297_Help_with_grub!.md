---
title: "Help with grub!"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-08-24
Hey, larwain ben-adar!  ya there?

Still need to post the menu.lst.  still need the instructions!

---

### Post by randell6564 on 2006-08-24
AHHH! remembered!

[B]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
[/B]

Hope this helps!

---

### Post by Iarwain ben-adar on 2006-08-24
Well, still need a little more info :D

What is the error that you get when you try to boot without live-cd?


Iarwain

---

### Post by randell6564 on 2006-08-24
> **Iarwain ben-adar said:**
> Well, still need a little more info :D

What is the error that you get when you try to boot without live-cd?


Iarwain

I'll reboot.  be back in a jiffy!

---

### Post by randell6564 on 2006-08-24
DAMN!  I DO kinda like this setup!  All I have to do is stick in the live cd to boot to either OS!

Without the cd the error is., [B]verifying DMI pool Data
Boot from cd:
Boot from cd:
Error loading operating system****[/B]

---

### Post by randell6564 on 2006-08-24
It didn't work my friend!  I dont know., maybe i can live with this!

---

### Post by Iarwain ben-adar on 2006-08-24
You're giving up already? :D

Well, if you want to...
but i googled a bit, and found it could be that it was something hardware related... (did you tingle with your pc recently?)


Iarwain

---

### Post by randell6564 on 2006-08-24
> **Iarwain ben-adar said:**
> You're giving up already? :D

Well, if you want to...
but i googled a bit, and found it could be that it was something hardware related... (did you tingle with your pc recently?)


Iarwain

Nope.,I Gurantee you that it is NOT hardware related.  Every ubuntu installation that I have done has been on this box.  And the Christian Edition is just ubuntu with a christian flavor.

Both of these installations work Beautifully.  They just wont boot without the cd! once I boot with the cd, I can remove it and everything is fine.

HA!! So., if I am the only one who knows where the cd is, I am the only one who can use this box!  HA!!

Thanks Iarwain! Hope to chat with ya soon!

---

