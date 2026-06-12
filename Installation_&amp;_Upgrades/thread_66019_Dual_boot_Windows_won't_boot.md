---
title: "Dual boot: Windows won't boot"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by monkie on 2005-09-15
Hey, well here is my problem. I have 2 hard ata133 hard drives on this system.

hdd1: ubunutu
hdd2: windows

hdd1 is the primary drive.

So I installed windows first on the second hard drive and it would only boot if I turned my primary hdd off in bios. So I then installed ubuntu and everything went fine. (I put grub on the first partition of hdd1)  But now I cannot boot up into windows. I have searched the forums on this matter over and over and have tried all the suggestions of tricking windows into thinking it is on the primary, but none have worked. Here is my current /root/grub/menu.lst

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
# kopt=root=/dev/hda3 ro

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
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
map (hd0)(hd1)
map (hd1)(hd0)
makeactive
chainloader +1
boot

Which gives the following error when I try to boot windows:
map (hd0)(hd1)
Error 11: Unrecognized device string
press any key to continue... 

which brings me back to the grub menu. Any suggestions would be helpful :)

---

### Post by xaverx on 2005-09-16
Try boot with installation cd of windows, run recorery console and type command fixmbr. Then windows write it on mbr his data. Then you should start windows. But not ubuntu. You must run installation of ubuntu and make boot from grub, or run rescue console of ubuntu, and type grub-install /dev/hda

---

### Post by Flegg on 2005-09-18
Hi there, after reinstalling windows MBR how do you access ubuntu's recovery console? if you reinstall all of ubuntu again, won't you be faced with the same original problem of ubuntu will boot but not windows?

I am having the same problem and I cannot get windows to boot where as windows is in the first partition and ubuntu in the 2nd

Thanks

Flegg

---

### Post by cotcot on 2005-09-19
I installed win98 first and then ubuntu (5.04). During the 5.04 install I selected to install grub on a floppy. Afterwards I made the win98 active in DOS with fdisk. Now when I boot with the floppy inserted I have any choice (5.04 and win98). Without the floppy (this is the kids-position for games) it gives directly win98. Maybe it works on XP too. (if not you vould try to install 5.xx with grub on floppy after the XP install and restore the XP MBR with the XP installation disk). Check if the bios sees the floppy first.
I hope this gives some inspiration.

---

### Post by xaverx on 2005-09-20
you can use live cd, command chroot /mnt/sysimage to mout disk and run grub-install /dev/hda

---

