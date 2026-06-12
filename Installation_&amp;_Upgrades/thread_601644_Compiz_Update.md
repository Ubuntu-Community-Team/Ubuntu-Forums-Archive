---
title: "Compiz Update"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2007-11-03
I just received an update notification for Compiz in Gutsy. Anybody test it yet?

---

### Post by Pumalite on 2007-11-03
I got it. No problems.

---

### Post by PmDematagoda on 2007-11-03
Same here, nothing bad happened.

---

### Post by th3gh05t on 2007-11-03
Something bad happened to my system. My system was fine after the update, but after I logged out, and logged back on, everything is weird.

- I can't right click on the desktop. The desktop image doesn't load. 

- The background for conky is messed up. Stays the same Ubuntu brown from when booting up.

- And my background image for my top panel doesn't want to display.

Check out the screen shot.

All the visual effects for compiz are running fine. Minimize, desktop cube, etc.

I'm going to do a restart and hopefully that will fix the problem.

---

### Post by lsutiger on 2007-11-03
Hey everyone who replied, what grapx card are you using?

Also, this is OT and has nothing to do with the update, but for some unknown reason I lost the splash screen with Ubuntu and the never ending 'progress bar'. Anybody know how to get that back?

---

### Post by PmDematagoda on 2007-11-04
I'm using an Nvidia 6200. And open up your menu.lst file using 

```
sudo gedit /boot/grub/menu.lst
```

and post the file here.

---

### Post by siegs01 on 2007-11-04
i updated compiz i have an Nvidia 6800 GT and now the i get the message "The display server has been shut down about 6 times."

---

### Post by Pumalite on 2007-11-04
I have Nvidia 6600 GS and 7800 GT among others and compiz is working fine in both of them.

---

### Post by lsutiger on 2007-11-04
I am using an ATI Xpress 1100.
Here is the menu.lst file:```
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
#color cyan/blue white/bluesudo gedit /boot/grub/menu.lst
-

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
# kopt=root=UUID=80854392-9914-4d68-918d-6da826a75872 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=80854392-9914-4d68-918d-6da826a75872 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=80854392-9914-4d68-918d-6da826a75872 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by lsutiger on 2007-11-04
anybody else?

---

### Post by gavinlao on 2007-11-04
I have BIG problem after install the Compiz update.. my computer cannot boot into X after install the update.. now it just can boot into command mode, I use intel 965gz onboard display, it runs very good before and can use desktop effect smoothly.

---

### Post by lsutiger on 2007-11-10
Bump!

Also - anybody has the same setup a me?

---

### Post by Pumalite on 2007-11-10
I tried Gutsy with an ATI 9200 SE and it's a no go.

---

