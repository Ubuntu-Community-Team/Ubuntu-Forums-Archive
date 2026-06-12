---
title: "multy booting is not work.."
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by pdk001 on 2005-04-29
hello
im a beginner to ubuntu(actually i haven't used kind of debian)
i've successed to build ubuntu up and work well
but im having a trouble how to install applications and something else
this machine isn't mine and sisters doesnt know anything at all
they use M$ everytime so this machine have to boot with M$ when turn on computer
it says "filesystem unknown when i choose the "windows XP" and doesnt boot with M$
help me out plz for my sisters
thanks in advance
great regards

---

### Post by odix on 2005-04-29
Please post your /boot/grub/menu.lst and and execute the following command:
```
sudo fdisk -l /dev/hda
```
replace /dev/hda with your harddisk, if you multiple hds run the command with all of the and post the results

odiX

---

### Post by pdk001 on 2005-04-29
here is my menu.lst

 - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by c_dog on 2005-04-29
Windows can only boot from the first hard disk. GRUB can get around this limitation though. To get GRUB to boot from the  second hard disk you need to trick Windows into thinking the second disk is the first  by remaping the order of the drives in the menu.lst file.

```
title windows
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0) +1

```

---

### Post by pdk001 on 2005-04-29
thanks so much for advice
i just checked it out and work well, thanks once again
but new title "windows" shows up in the grub menu list when i booting
and it dosent even work when i choose it "windows" in the grub menu list
but "Microsoft Windows XP Professional" does work 
i want two titles in the list
is this not mind if i delete "title windows"?

---

