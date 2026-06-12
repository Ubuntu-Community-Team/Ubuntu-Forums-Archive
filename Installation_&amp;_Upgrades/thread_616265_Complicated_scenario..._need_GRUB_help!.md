---
title: "Complicated scenario... need GRUB help!"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by tC_Crazy on 2007-11-18
So my scenario is this: I had 3 windows XP partitions, one is a 58GB for "storage" one is 10GB for the OS, and one 80GB for "multimedia." However, the storage did have an old XP install which i don't use anymore.

I decided to install Ubuntu. After tons of problems with partitions, I figured out the only way to make it work without reinstalling windows or wiping my hard drive clean. I put the 3 NTFS windows partitions into an extended partition and made them logical. Then I made a primary "boot" partition, a linux ext3 partition, and a swap partition. Ubuntu works, (albeit slow... thats a whole nother problem) but XP does not. When I go to Windows XP Home on GRUB, it gives me Error 12. 

Here's my fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4dcb4dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           4       32098+  83  Linux
/dev/sda2               5       18183   146022817+   f  W95 Ext'd (LBA)
/dev/sda3           18184       19330     9213277+  83  Linux
/dev/sda4           19331       19457     1020127+  82  Linux swap / Solaris
/dev/sda5               5        7649    61408431    7  HPFS/NTFS
/dev/sda6            7650        8924    10241406    7  HPFS/NTFS
/dev/sda7            8925       18183    74372886    7  HPFS/NTFS


AND here's my grub/menu.lst
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
# kopt=root=UUID=416d2a4f-6a3a-4ea3-8a29-d39ddafb404e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
kernel		/vmlinuz-2.6.22-14-generic root=UUID=416d2a4f-6a3a-4ea3-8a29-d39ddafb404e ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=416d2a4f-6a3a-4ea3-8a29-d39ddafb404e ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Home Edition
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
rootnoverify		(hd0,5)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Windows NT/2000/XP (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1


I added noverify to root, and the map as per another post's directions. Neither have helped.

Any ideas?

---

### Post by meierfra on 2007-11-18
In general you cannot boot windows from a logical partition. But since you copied it from a primary partition where might be some chance to get it to boot. Remove all the "map" statements and also the "makeactive" ( grub  returns  an error if you  apply "makeactive" to a logical partition.)

It would have  been much better to leave the windows OS partitions as primary, and put ubuntu and swap on the extended partition.

You might also want to check out this link:

[http://www.goodells.net/multiboot/index.htm]("http://www.goodells.net/multiboot/index.htm")

---

### Post by tC_Crazy on 2007-11-18
Hey thanks a lot! I got it up and running flawlessly now. I removed the map statements and makeactive. Then I reconfigured the Windows boot.ini to reflect the new partitions, and it now boots. 

And CompizFusion is so cool!!!! haha

---

### Post by meierfra on 2007-11-18
```
Hey thanks a lot! 
```

You are welcome.  And I  need to thank you, too. I have never seen anybody at the ubuntu forums who got this to work. I only knew it was theoretically possible ( from the link I posted in my previous post).

---

