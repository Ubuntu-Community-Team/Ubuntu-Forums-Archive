---
title: "Dual Boot SATA / IDE: SIMPLE SOLUTION FOUND!!!"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by dgcarter on 2007-07-13
Ok, after much reading, googleing and scratcing around I have finally found the solution to my problem.

SITUATION:

SATA HDD: Has windows XP install already
IDE HDD: Wanting to install Ubuntu 6.06 LTS

PROBLEM:

GRUB won't install on SATA HDD over the XP MBR
Linux fails to boot either OS

SOLUTION:

Step 1:
Unplug all HDD's except the IDE drive which will have linux installation

Step 2:
Install Ubuntu as usual

Step 3:
Shut down, plug all HDD's in again

Step 4:
Make sure you set BIOS to boot from the IDE HDD with your linux installation 1st

Step 5:
Once Ubuntu boots, edit the /boot/grub/device.map so it reads as follows
(based on my HDD configuration)

```

(hd0)	/dev/hda
(hd1)	/dev/sda

```

(hd0) is my primary master IDE drive
(hd1) is my SATA drive with windows XP installed

Step 6:
Edit the /boot/grub/menu.lst so it reads as follows
(based on my HDD configuration)

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
timeout		3

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title		Windows XP Professional
map 		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify	(hd1,0)
chainloader	+1
makeactive
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I changed the following:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Comment out the hidemenu, so u won't have to press Esc to access the boot menu

I added the XP boot section:

```

title		Windows XP Professional
map 		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify	(hd1,0)
chainloader	+1
makeactive
boot

```

The map (hd0) (hd1),  map (hd1) (hd0) lines seemed to do the trick. I now get a menu which gives me 3 seconds to choose either Ubuntu or XP.

PHEW! :KS

---

### Post by dabl on 2007-07-13
I had a variation of the problem -- I wanted to use the first SATA drive for a small Win XP installation, and also for Kubuntu, and leave the IDE drive for different purposes/OSs.  Here's the story (pasted from another forum):

I built this system on an Intel D975XBX motherboard, hung an IDE drive and 2 SATA drives on it, and spent 3 days trying to convince Kubuntu Edgy that it would be OK to put Grub on one of the SATA drives.  Big waste of time!  I'm not sure if it is a BIOS bug or a Linux bug, and it really doesn't matter much as long as you understand the behavior and adapt your system to deal with it.

I eventually fdisked all 3 hard drives, then first installed Windows XP on a partition on the same SATA drive where I also wanted to install Kubuntu, leaving the IDE drive unpartitioned and unformatted.  With that done, I used the "Alternate Install" Kubuntu CD to install Linux, and when it got to the point of installing Grub, it was happy to use the mbr where it saw the Windows bootloader.  So that's how I "fooled" it into doing things my way.  Your mileage may vary, of course ....

:)

---

### Post by dgcarter on 2007-07-13
I thought about installing linux and windows on the same SATA drive, as i have more than enough space, but I could not find anything to resize my existing NTFS partition as it currently takes up the whole drive and I didn't want to format. So I'm glad this worked for me.

---

