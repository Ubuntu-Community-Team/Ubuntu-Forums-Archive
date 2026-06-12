---
title: "Grub menu items invisible"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by Cuppa-Chino on 2006-08-13
Hi all,

got a strange behaviour in the grub menu. Only the first line is highlighted and the other items only become visible when I have cursor'ed up and down. Any ideas?

here my menu.lst
```
splashimage (hd0,2)/boot/grub/images/fiesta.xpm.gz
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
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color dark-gray/blue light-blue/light-gray

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
# kopt=root=/dev/sda3 ro

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

##### 
title		Windows XP by his Billyness
root		(hd0,0)
makeactive
chainloader	+1

title
root

#####
title 		Current Kernels
root


title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot


title
root
#####
title 		Old Kernels
root		

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

#title		Ubuntu, kernel 2.6.15-25-686
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/sda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-25-686
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-25-686 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/sda3 ro single
#initrd		/boot/initrd.img-2.6.15-25-686
#boot

#title		Ubuntu, kernel 2.6.15-25-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-25-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda3 ro single
#initrd		/boot/initrd.img-2.6.15-25-386
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

#title		Ubuntu, kernel 2.4.27-2-686-smp
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.4.27-2-686-smp root=/dev/sda3 ro quiet splash
#initrd		/boot/initrd.img-2.4.27-2-686-smp
#savedefault
#boot

#title		Ubuntu, kernel 2.4.27-2-686-smp (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.4.27-2-686-smp root=/dev/sda3 ro single
#initrd		/boot/initrd.img-2.4.27-2-686-smp
#boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST




```

pls no flaming that Windows is the first item.... and not that does not matter whether I have splash image or not...

thanks

---

### Post by Tomosaur on 2006-08-13
Very odd indeed. If I have a splash image and custom colours together, I get similar behaviour, although I can still see the menu items. I just don't see the highlight. However, since you only have a splash image enabled (and not colours), I can't think why this would be happening.

I do see that you have a totally empty menu item however, just underneath your windows one. I would recommend you get rid of that and see what happens, maybe Grub's getting confused.

---

### Post by Cuppa-Chino on 2006-08-13
Hi thanks will try that, also you editor looks well cool

---

### Post by Tomosaur on 2006-08-13
Thx2u :)

---

### Post by Cuppa-Chino on 2006-08-16
the empty lines were the problem! that was it, now working fine

:KS

---

