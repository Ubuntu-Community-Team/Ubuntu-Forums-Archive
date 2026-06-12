---
title: "Vista SP1 wipes out grub/ubuntu on load"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by art_s on 2008-05-10
Hi all,

It's really weird, but:

I've installed Ubuntu (8.04) and on the first load got Grub screen with two Vistas listed.

If I select either of those, vista starts loading its system restore procedure, which end us displaying huge red ERROR word in some sort of broken window. And, of course, it dies.

Rebooting after that gives grub 22 or 17 error (I got different ones after couple of reinstalls).

If I don't load vista first and just start Ubuntu, it's all good.
But as soon as I try to load windows - it stuffs everything up.

Please help!

Thanks

---

### Post by Pumalite on 2008-05-10
Post:
sudo fdisk -l

---

### Post by art_s on 2008-05-10
Thanks for your uberprompt reply!

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bef74b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8192000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1021        7313    50548522+   7  HPFS/NTFS
/dev/sda3            7314       15823    68356575   83  Linux
/dev/sda4           15824       30402   117100090+   f  W95 Ext'd (LBA)
/dev/sda5           16221       30402   113905664    7  HPFS/NTFS

---

### Post by Pumalite on 2008-05-10
Post:
cat /boot/grub/menu.lst (from sda3)

---

### Post by art_s on 2008-05-10
> **Pumalite said:**
> Post:
cat /boot/grub/menu.lst (from sda3)
Sorry, how do I do that?
Tried that in sudo grub,
it gave

"grub> cat /boot/grub/menu.lst

Error 12: Invalid device requested"

tried 

grub> device /dev/sda3

Error 11: Unrecognized device string

---

### Post by Pumalite on 2008-05-10
Sorry;
sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
cat /media/sda3/boot/grub/menu.lst

---

### Post by art_s on 2008-05-10
Actually, I think I managed to mount it... :)
Bot the file is pretty big though...

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
# kopt=root=UUID=ed761946-10e7-4c11-b295-3a7bbe5c6fc6 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ed761946-10e7-4c11-b295-3a7bbe5c6fc6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ed761946-10e7-4c11-b295-3a7bbe5c6fc6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

---

### Post by Pumalite on 2008-05-10
Edit your menu.lst. Remove the first instance of Vista. Change to #groot=(hd0,2). Change the 'root' line of Ubuntu to (hd0,2). Save, exit, reboot.

---

### Post by art_s on 2008-05-10
> **Pumalite said:**
> Edit your menu.lst. Remove the first instance of Vista. Change to #groot=(hd0,2). Change the 'root' line of Ubuntu to (hd0,2). Save, exit, reboot.

I removed second instance of vista, leaving only this one:

title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

I also changed all Ubuntu instances to 
root		(hd0,2)

not sure what you mean on "#groot=(hd0,2)"

I restarted, but it didn't make a difference

---

### Post by Pumalite on 2008-05-10
How did you partition to create sda3?

---

### Post by art_s on 2008-05-10
> **Pumalite said:**
> How did you partition to create sda3?

I think I selected "manual" and created 70Gb partition for "/" and another 3Gb for swap.

I tried "use free space" setting when running install for the first time, but it got stuffed up in the same way

---

### Post by Pumalite on 2008-05-10
When you use Vista; you have to allocate free space for Ubuntu with the Vista partitioner. You cannot partition with the Ubuntu CD. Give thanks to Microsoft.

---

### Post by ThaDiggler on 2008-05-10
Got to [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and make a super grub cd.  It will guide you on how to repair your grub menu.

---

### Post by art_s on 2008-05-10
> **Pumalite said:**
> When you use Vista; you have to allocate free space for Ubuntu with the Vista partitioner. You cannot partition with the Ubuntu CD. Give thanks to Microsoft.

Damn I knew there was something wrong with that!
It didn't let me to resize vista partition to the size less than 40Gb, and I though I will fool it with Partition Editor... Damn!

Thanks for your help guys!

---

### Post by Pumalite on 2008-05-10
Good luck.

---

