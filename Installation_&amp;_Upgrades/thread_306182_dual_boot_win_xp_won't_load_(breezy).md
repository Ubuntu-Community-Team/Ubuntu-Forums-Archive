---
title: "dual boot win xp won't load (breezy)"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by michaeljoe on 2006-11-24
Greetings all.  Until recently I had a working dual boot for Breezy and Win XP.  I decided to resize/modify some of my partitions and ever since, I am unable to load Win XP.  I get the message:

 'Filesystem Type Unknown, Partition Type 0x7'.

I've been reading threads from users getting the same message and have tried some of the solutions suggested, but haven't yet been successful.  I'd rather not reinstall everything unless I have to.  I'm relatively new to Linux and Grub.  Anyone have a suggestion?

Below are the contents of /boot/grub/menu.lst and fdisk:

(you'll notice I've commented out some of the Win XP startup lines based on 'solutions' I've seen posted in other threads)

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
timeout		30

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb5.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb5.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb5.
title		Ubuntu, memtest86+ (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb5.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hda3) (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb5.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda3) (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb5.
title		Ubuntu, memtest86+ (on /dev/hda3) (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, memtest86+ (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
##savedefault
##makeactive
##map		(hd0) (hd1)
##map		(hd1) (hd0)
chainloader	+1

====================================================================
sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            2238        4863    21093345    5  Extended
/dev/hda2            1022        2237     9767520   83  Linux
/dev/hda3   *           1         975     7831656   83  Linux
/dev/hda4             976        1021      369495   82  Linux swap / Solaris
/dev/hda5            2238        4863    21093313+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         561     4506201    7  HPFS/NTFS
/dev/hdb2             562        1060     4008217+   5  Extended
/dev/hdb3            1061        1245     1486012+  83  Linux
/dev/hdb5             562        1047     3903763+  83  Linux
/dev/hdb6            1048        1060      104391   82  Linux swap / Solaris


MJ

---

### Post by confused57 on 2006-11-24
What kind of partition changes did you make?

In your Windows entry, you definitely need the 2 lines with "map", you don't need the "savedefault", may or may not need "makeactive"...

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
##savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If you haven't installed grub to your slave drive(hdb), have you tried connecting it as master(disconnect your other drive) and booting.

---

### Post by michaeljoe on 2006-11-24
It was a while back, but I believe I just resized some of the partitions.  That's what I get for experimentation but, ah well, gotta learn somehow.  I have 2 hard drives.  Breezy loaded on one (hda partition 3) and WinXp loaded on the other (hdb partition 1).

I could reinstall everything, and I don't mind doing that...BUT I really don't want to go thru getting my wireless adapter configured again.  Is there an easy way to save the wireless settings, then re-install, then load the wireless settings back in?

MF

---

