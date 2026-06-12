---
title: "Re: Error 12: Invalid device requested**NEED HELP****"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by Albundy213 on 2007-12-14
Hi all,
I finally decided to give up and post a question that most likely has been answered but I just can't seem to get this going. Here it is. I have 3 hard drives. One has XP, second has Ubuntu and last is just for storage. I'm listing my fdisk and my menu.lst. My problem is every time I boot up to Grub and pick windows to Boot I get this "Error 12: Invalid device requested" I been trying to figure this out all day long and I don't know what to do anymore. If someone can please show me the way I will be most grateful.

**Boot menu............**


# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=19398579-d1a3-4bb9-bb4d-bbee36a5b996 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=19398579-d1a3-4bb9-bb4d-bbee36a5b996 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=19398579-d1a3-4bb9-bb4d-bbee36a5b996 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


Disk Drives..................

Disk /dev/sda: 250.0 GB, 250059350016 bytes
102 heads, 51 sectors/track, 93886 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x00000001

Device Boot Start End Blocks Id System
/dev/sda1 * 1 51601 134214175+ 7 HPFS/NTFS

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fad8

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 36482 293041633+ 83 Linux
/dev/hdc2 36483 37211 5855692+ 82 Linux swap / Solaris

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x045fcd7e

Device Boot Start End Blocks Id System
/dev/hdd1 * 2 9729 78140160 f W95 Ext'd (LBA)
/dev/hdd5 2 9729 78140128+ 7 HPFS/NTFS
charlie@charlie-desktop:~$

---

### Post by Pumalite on 2007-12-15
Where is hdb?Or sdb?
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Pumalite on 2007-12-15
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)
This usually happens when trying to boot Windows in a logical partition.

---

### Post by Albundy213 on 2007-12-15
Thanks for the links PUMA, I been waiting for some kind of response since I posted my comment. I will go through each and pray I'm able to find a way to make this work. I been trying this for days now, obviously I'm no Ubuntu expert or even close to being one but I'm trying slowly but easy. Also you kind of lost me on your question "Where is hdb?Or sdb?" Not really sure what kind of output you need to see. Just tell me the command to run and I'll post it.

Thank You.

---

### Post by Pumalite on 2007-12-15
Don't worry; just make sure you install Windows first and Ubuntu last and that you install Windows in a primary partition.(likes to be sda1)

---

### Post by psusi on 2007-12-15
Is it the 80 gig or the 120 gig drive that has windows installed?

When you are at the grub menu, press e to edit the commands.  Try changing the (hd2 part to (hd1 and press b to boot.  Also you might try hd0.

---

### Post by Albundy213 on 2007-12-16
Thanks for the help guys. I finally was able to get the darn thing to work. All I did was change the hd2 part to hd1, that simple. Amazing I spent countless hours trying to figure this out and just like that it worked out. Hopefully this can help out the next person attempting or having the same problem as I encountered,

---

