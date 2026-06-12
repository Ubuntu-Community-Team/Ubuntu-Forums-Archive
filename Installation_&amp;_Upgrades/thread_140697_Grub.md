---
title: "Grub"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by SVFUSiON on 2006-03-06
GRUB fails to boot any of my OSes, however i can edit the .lst with the live cd. I have looked everywhere I can not seem to figure this out. I am been trying the whole weekend. here is my .lst.

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
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdd2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdd2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

here is my list of partitons

  Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               3       79889    40262656    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdd2   *       79895      151933    36306900   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hdd3          151933      155056     1574370    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hdd5          151933      155056     1574338+  82  Linux swap / Solaris

Please help lol.

---

### Post by Sutekh on 2006-03-06
Whats in this file?  

/boot/grub/device.map

It looks like Windows and Linux are on hdd, yes?

So the device.map will tell you what hdd is *mapped* to, which is the location GRUB uses in the menu.lst.  

It may look like this

(hd0) /dev/hdd

In which case to boot Ubuntu, you need the line **root (hd0,1)** not (hd1,1)

And Windows to be **root (hd0,0)** not (hd2,0), BUT this depends on the contents of the device.map

---

### Post by SVFUSiON on 2006-03-06
well nothing now, I have really messed things up! I tried to make a new MBR with a Windows 98 CD, BAD IDEA, then I reinstall Ubuntu to see if it would install grub and locate the Vista Installtion on the other partiton, it didnt. All i have when I boot that HDD is "NO OPERATING SYSTEM FOUND". Now what do I do? :confused:

---

