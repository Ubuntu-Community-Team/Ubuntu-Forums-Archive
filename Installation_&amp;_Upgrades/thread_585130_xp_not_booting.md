---
title: "xp not booting"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by roystonvasey on 2007-10-21
My gutsy install went just great. I've been using it for a couple days with no problem. Now I need to do some work in XP. So I select the XP loader in the grub menu and wait for XP to boot, but all I get is the "Starting up . . ." text and nothing happens. I'm wondering if something isn't goofy in my grub menu list? Thanks for any help!

Here's my grub file:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

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
# kopt=root=UUID=964e2f03-db10-44ed-9007-71292d815bd9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=964e2f03-db10-44ed-9007-71292d815bd9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=964e2f03-db10-44ed-9007-71292d815bd9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sdb1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2caa936b-0206-42b3-af74-930aa20706ac ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2caa936b-0206-42b3-af74-930aa20706ac ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2caa936b-0206-42b3-af74-930aa20706ac ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2caa936b-0206-42b3-af74-930aa20706ac ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sdb1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by Pumalite on 2007-10-21
Post:
sudo fdisk -lu

---

### Post by roystonvasey on 2007-10-21
fdisk -lu gives me:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21aa61fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   155220029    77609983+   7  HPFS/NTFS
/dev/sda2       155220030   312576704    78678337+   f  W95 Ext'd (LBA)
/dev/sda5       155220093   312576704    78678306    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ac36900

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    61432559    30716248+  83  Linux
/dev/sdb2        61432560    81915434    10241437+  82  Linux swap / Solaris

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10d110d1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   149838254    74919096   83  Linux
/dev/hda2       149838255   156296384     3229065    5  Extended
/dev/hda5       149838318   156296384     3229033+  82  Linux swap / Solaris


```

---

### Post by Pumalite on 2007-10-21
Try changing this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

To this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Make the change, save, exit, and reboot
Let's see

---

### Post by roystonvasey on 2007-10-21
no go :( that gives me this error:

```
Error #13: Invalid or unsupported executable format
```

thanks for helping me out here!

---

### Post by Pumalite on 2007-10-21
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)
Explain to me where, to your knowledge you have each of the OS

---

### Post by roystonvasey on 2007-10-21
is this what you mean?

drive 1: ide with gutsy
drive 2: sata with xp
drive 3: sata with feisty

that link you sent makes me think maybe my windows bootsector might be corrupted. what do you think about that? or maybe i should re-jigger my set up so that the ide with gutsy is after the xp in the disk hierarchy? i think the ide is set to master.

---

### Post by roystonvasey on 2007-10-23
I investigated my windows boot sector with TestDisk and that came back with no problems. Anyone have any ideas? Can I make my IDE drive come after the SATA drives in priority?

---

