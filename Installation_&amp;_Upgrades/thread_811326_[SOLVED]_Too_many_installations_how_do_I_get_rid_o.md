---
title: "[SOLVED] Too many installations how do I get rid of them?"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2008-05-29
Folks,

First of all, many apologies for the long windedeness of this posting.

I originally posted a query on the Absolute Beginner forum and now I'll try here.

Some time ago I managed to install version 7.10 on my ASUS laptop which already contained Windows XP which I unfortunately need for some particular applications that will only run on Windows.

I sent for and received the new 8.04 version cd and installed it thinking (incorrectly it would appear), that it would install over the older version. What of course occurred was that I now have versions 8.04 and 7.10 plus XP. In fact from the information shown when I first switch on I may even have inadvertently installed 8.04 twice.

What I am trying to find out is how to remove any and all versions that I don't need, delete any partitions that will become vacant as a result of removing these versions and how to let linux get access to any free disk space that results from these deletions.

I've noted all of the replies to my posting but am still in the dark. My problem is that I seem to have somehow installed the new version (8.04) at least twice.

This has probably occurred because I have inserted the new cd more than once and simply followed what appeared to be the most obvious menu option (install).

I have also noted one reply that told me to delete part of the /boot/grub/menu.lst file, which I eventually located. However, when I attempt to do this, the text editor option under the Applications menu item informs me that I do not have permission to perform a save operation after attempting to perform the deletion.

In addition, the same reply that discusses deleting part of the /boot/grub/menu.lst file mentions that when I've completed the deletion I can then delete the offending partition.

Therein lies the problem. Which partition do I delete, there appears to be several. This was my original problem as can be seen from my original posting.

Perhaps one of the many gurus can explain exactly how I can get out of my dilemma in words that a absolute beginner can understand.

I'm attaching my /boot/grub/menu.lst and a screen shot of the results shown in the gnome partition editor

Any assistance will be gratefully accepted.

Regards,

Bob

XXXXXXXXXXXXXXXXXX
My /boot/grub/menu.lst file contents are:

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
# kopt=root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by zvacet on 2008-05-29
If you want to delete Gutsy delete hda3 partition.Boot your live CD and start Gparted.Simply choose hda3 and delete it.You will get unallocated space which you can add to hda6 for example.

---

### Post by meierfra. on 2008-05-29
You only  have one Hardy installed. What you see one your Grub menu are different kernels. (The kernel has been updated in last few days) Ubuntu does not delete the old kernels, because it can happen that the new kernel is incompatible with your hardware.    Since the new kernel seems to be working for your, you can simple deleted this part

> title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro single
initrd /boot/initrd.img-2.6.24-16-generic



of your "menu.lst" Or you can put a "#" in  front of each of those line.


I actually just leave two sets of kernels on  my menu.lst. But since I do not want more than two sets, I changed

"#howmany all " in menu.lst to "#howmany 2".


Some people use "sudo apt-get remove ..." to physically remove their old kernels, but since they don't take up much  hard disk space, I just keep them.


And if you want to delete Gutsy just follow zvacet advice.  You can deleted the Gusty entry



> # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title Ubuntu 7.10, memtest86+ (on /dev/hda3)
root (hd0,2)
kernel /boot/memtest86+.bin
savedefault
boot



 from your menu.lst  before or after you deleted Gusty, it does not matter.

---

