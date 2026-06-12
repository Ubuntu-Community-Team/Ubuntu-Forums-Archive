---
title: "loading XP + ubuntu?"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by master.durin on 2005-04-23
I have hd with 2 logical disks. I had win98 on disk C and winXP on disk D, after that i formated disk C  and installed ubuntu there, disk D still contains Windows XP. After i installed ubuntu i can`t load XP. i changed "menu.lst" but it still doesn`t load XP.
Is it possible to load XP from disk D? 

here is my menu.lst file:
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,5)
savedefault
makeactive
chainloader	+1

---

### Post by seven on 2005-04-23
Maybe windows installed the boot loader on drive C:
try to install a new one by booting XP install disk, entering a recovery console
and writing 
fixmbr D:
fixboot D:

(check if the driver letter still remianed D)
it may help, it worked on my old PC

---

### Post by master.durin on 2005-04-25
thank you, I'll try it

---

### Post by c_dog on 2005-04-25
I don't think that your MBRs need fixing, at least not as far as Windows or Linux is concerned. 

Windows doesn't like being anywhere except the primary master drive. No matter what boot loader you use, you will need to trick Windows temporarily into thinking that it is on the primary master or it will not boot. 

First, you may want to change "root" to "rootnoverify" (though I don't think you need to.)

Add this before your chainloader command:

```
map (hd0) (hd1)
map (hd1) (hd0)
```

This will temporarily switch the primary master and primary slave drives in bios. Any time you want to boot Windows from Grub on any secondary drive you will need this. I think you keep the root command pointed at (hd1,0).

---

### Post by mandy2tom on 2005-05-05
This is how I dual boot using windows boot loader with 2 drives
 

[http://ubuntuforums.org/showpost.php?p=159193&postcount=44](http://ubuntuforums.org/showpost.php?p=159193&postcount=44)

---

### Post by helder on 2005-05-09
hello all, Im a Newbie, so make your suggestions clear please  :)  so heres the question, I have Win xp installed with two partitions, and i will buy a HD to install UBUNTU, how do I make dual boot of Win xp and UBUNTU??





thank you!!!!

---

