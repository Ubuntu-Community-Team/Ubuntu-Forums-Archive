---
title: "Two Hard Discs Dual Boot: How?"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by zamboni on 2007-05-30
Hello;


I 'm doing something wrong, but I don't know what. here is what I want to accomplish:

 1) Have Slackware boot from hda (it already does this) Lilo boots hda fine.

 2) Have Ubuntu boot from hdb using grub. Haven't been able to get this to work yet.

Here is what I have tried so far:

I have installed  Ubuntu 7.04 on my second drive. I used the both the  X based installer and the alternate, and  tweaked the install to put the bootloader on  the second drive: hd1 (advanced button found in the partitioning dialog). The install went okay. However, when I rebooted, something went wrong. I can see a copy of the  kernel in the /boot folder, and listed in the /boot/grub/menu.lst . Choosing the kernel from the boot menu returns this message: Error 15: File Not Found. I have repeated the wipe drive/install process 6 times, and the same thing happens. 

I also did the same install procedure using the alternate iso. Same thing. Error 15 message. and I also tried the second drive as a master, hdc in linux parlance, repeating the install process with both the X installer and the the alternate iso.  Same thing. Error 15 message.

I wonder what I'm doing wrong or missing?

any clues, pointers most welcome


Thanks for reading

PS

below is the install generated menu.lsy file as found in /boot/grub.

maybe someone can spot the trouble there.

Thanks again

ps

I'm new to ubuntu but have used slackware since slackware 1.05


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
# kopt=root=UUID=0e4baded-ecc6-4de2-b39a-bafcc2cd0a22 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0e4baded-ecc6-4de2-b39a-bafcc2cd0a22 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0e4baded-ecc6-4de2-b39a-bafcc2cd0a22 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Slackware Linux (Slackware 11.0.0) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 
savedefault
boot

---

### Post by confused57 on 2007-05-30
Boot first to your Ubuntu drive, you should get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd1,0) to (hd0,0), then press "b" to boot...this "should" boot your Ubuntu, which is a temporary fix, if it works you can make it permanent in your /boot/grub/menu.lst.

Added:  You should be able to boot Slackware from grub, by changing the Slackware root to (hd1,0).

---

### Post by dabl on 2007-05-30
IMO, you are making this harder than it needs to be.

"Last Linux wins" is the rule I follow, being incompetent to manually place Grub (or do a lot of other things ...).

You need to pick one of your drives, mark your chosen partition "bootable" (I use the GParted Live CD for partitioning), and then let that be the residence for Grub.  The first Linux you install, presumably on that drive, will install Grub there.  Then second Linux you install, presumably on the second drive, will overwrite it and be the owner of the "master" version of /boot/grub/menu.lst.  But it will (or should) identify and place the first OS on the boot list, lower down of course.  If you want a Windows partition, do that installation first, and where it puts the Master Boot Record will be where the Grub file lives.

The gurus can tell you how to make a Grub Super Disk, edit the daylights out of files here and there, and beat the system.  But, for noobs, "Last Linux Wins" is the simple way.

:D

---

### Post by zamboni on 2007-05-30
Hey! Thanks! That did the trick....


But I'm still confused. I thought  hd0=hda and hd1=hdb or whatever the second physical hard disc happened to be. Changing hd1,0 to hd0,0 to my understanding means that grub is now looks at the first drive. Here's what I obviously have wrong. I will eventually get used to the notation.

Man after 7 installs, thanks again!

 

> **confused57 said:**
> Boot first to your Ubuntu drive, you should get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd1,0) to (hd0,0), then press "b" to boot...this "should" boot your Ubuntu, which is a temporary fix, if it works you can make it permanent in your /boot/grub/menu.lst.

Added:  You should be able to boot Slackware from grub, by changing the Slackware root to (hd1,0).

---

### Post by zamboni on 2007-05-30
Thanks for the input.

I certainly did and still have  the appropriate partitions bootable on each drive.  linux fdisk does this nicely.

Grub is a new animal to this  new ubuntu user. 

My approach is to have each drive as mutually exclusive installs. I do not want any automated ability to boot  slackware via grub, nor ubuntu via lilo.  Hardly a complicated affair once I get familiar with grub and its myriad of options.

thanks again

cheers!


> **dabl said:**
> IMO, you are making this harder than it needs to be.

"Last Linux wins" is the rule I follow, being incompetent to manually place Grub (or do a lot of other things ...).

You need to pick one of your drives, mark your chosen partition "bootable" (I use the GParted Live CD for partitioning), and then let that be the residence for Grub.  The first Linux you install, presumably on that drive, will install Grub there.  Then second Linux you install, presumably on the second drive, will overwrite it and be the owner of the "master" version of /boot/grub/menu.lst.  But it will (or should) identify and place the first OS on the boot list, lower down of course.  If you want a Windows partition, do that installation first, and where it puts the Master Boot Record will be where the Grub file lives.

The gurus can tell you how to make a Grub Super Disk, edit the daylights out of files here and there, and beat the system.  But, for noobs, "Last Linux Wins" is the simple way.

:D

---

### Post by confused57 on 2007-05-30
> **zamboni said:**
> Hey! Thanks! That did the trick....


But I'm still confused. I thought  hd0=hda and hd1=hdb or whatever the second physical hard disc happened to be. Changing hd1,0 to hd0,0 to my understanding means that grub is now looks at the first drive. Here's what I obviously have wrong. I will eventually get used to the notation.

Man after 7 installs, thanks again!
Whichever drive is selected to boot first in bios is designated as (hd0) when you install grub...when you boot first to /dev/hdb, then hdb is (hd0), but you need to edit your /boot/grub/menu.lst manually.

Here's an excellent guide with everything you need to know about grub:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
See the grub page section.

Also, you'll need to change the groot line in grub to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

