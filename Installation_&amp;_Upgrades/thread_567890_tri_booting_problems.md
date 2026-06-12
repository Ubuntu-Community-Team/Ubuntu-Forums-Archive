---
title: "tri booting problems"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by reloadSE on 2007-10-05
well i tried to tri boot windows vista fedora 7 and ubuntu 7.04

This is the way i installed it: Vista (preinstalled)->fedora7->ubuntu 

with ubuntu's grub i cannont boot into fedora or vista but i can boot into vistas recovery partition just too watch it lock up...

heres sudo fdisk -lu 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      144585   235994849   117925132+   7  HPFS/NTFS
/dev/sda2       265425930   299564054    17069062+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3       299564055   312576704     6506325    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4       235994850   265425929    14715540   83  Linux
/dev/sda5       266807583   267016364      104391   83  Linux
/dev/sda6       267016428   299564054    16273813+  8e  Linux LVM
/dev/sda7       265426056   266807519      690732   82  Linux swap / Solaris

could someone help please?

---

### Post by reloadSE on 2007-10-05
Any one????

---

### Post by Jose Catre-Vandis on 2007-10-05
Do you get the grub menu?

If so you should be able to edit the entries in order to boot the two linux distros

If you have a live cd, use that to get to your ubuntu installations menu.lst file, and print it here for more help

---

### Post by leopex on 2007-10-05
Cant u just reinstall GRUB/LILO? Just get the partitions right first :P

---

### Post by reloadSE on 2007-10-05
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
# kopt=root=UUID=e086f786-c510-4757-913f-0f11c513fcc7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e086f786-c510-4757-913f-0f11c513fcc7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e086f786-c510-4757-913f-0f11c513fcc7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista recovery (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

There ya go Jose Catre-Vandis
I can with the super grub disc @ leopex but it doesnt boot vista... and if i restore it too fedora or ubuntu they dont boot each other.... just before i restored it too ubuntu and it wouldnt boot....

---

### Post by reloadSE on 2007-10-05
could someone please reply i really need my computer to work again.... thanks

---

### Post by Jose Catre-Vandis on 2007-10-07
Hmmm, no mention of Fedora at all in your menu.lst. Can't see why Vista won't boot, everything seems in order there.

So just to recap, you can boot ubuntu on /dev/sda4?

Where is fedora /dev/sda5?
if so, mount that partition, browse to the Fedora menu.lst, and copy over the boot option to your ubuntu menu.lst.

You might need to change the Vista entry. Edit menu.lst as follows:

Change this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
```

to this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

If none of this works, try updating grub to see if that helps

Live CD boot
at desktop open terminal and type the following:
```
sudo grub
```
this gives grub prompt, then
```
find /boot/grub/stage1
```
this will confirm the location of the grub info, (in this case should be (hd0,0)?)
next command use this info
```
root (hd0,0)
```
install grub to mbr
```
setup (hd0)
[code]quit
```
and reboot


If you have an alt cd try reinstalling grub (best page i can find about grub)

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

