---
title: "Grub error  21  + menu.list"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by linuxfan128 on 2006-07-28
I  recently installed a new hardrive in my Pc  and  put ubuntu on it. When i restart  i get a error 21. windows xp is on  hda ubuntu is on hdd. Here is my menu.list of my  ubuntu partition.


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows Whistler Personal
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```
please help me if you can

---

### Post by OpsVentus on 2006-07-28
Hello 128,

Error 21 is "cannot find disk".
I think you have installed Ubuntu and then added another disk?

Try to reinstall Grub, have a look at this.
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Cheers,
Bart.

---

### Post by asfaltboy on 2006-09-18
I have the same seemingly simple problem..
I reinstalled my hdisks and i dont remember the exact position of each drive.. can't login into windows can't into ubuntu.. i recived some errors about GRUB installation failure (details: [http://doc.gwos.org/index.php/Talk:Restore_Grub)](http://doc.gwos.org/index.php/Talk:Restore_Grub))..

Any ideas what i should try now ? I can try repairing winxp and use it's bootloader to log into windows and then try to sort things out from there ?

---

### Post by OpsVentus on 2006-09-18
If it used to work and you just switched drive positions, you could try to switch drive sequence. Grub should still be on one of the disks.

Cheers,
Bart.

---

### Post by asfaltboy on 2006-09-18
Thanks m8 :) but I already thought that the first time i got the message and i tried connecting my drives in every possible way possible and without any success (note: some1 should make grub more flexible with drive positions/sequence so it tries to detect changes?)..

Anyway problem is solved.. I downloaded & installed the drake 6.06 and just formatted my linux drive/partitions.. after that everything works perfectly.. I needed a clean slate anyway :P!

---

