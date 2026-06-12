---
title: "Grub cannot start windows xp from second partition"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by tjksn on 2007-12-16
Installed feisty on my PC that has XP on the second partition.  After install Grub did not automatically find the XP operating system so I edited menu.lst to include it.  My fstab and menu.lst files are below.  Any idea why it won't load?  The error I get is invalid device requested.  I am still a newbie at this so any input will be appreciated.

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
# kopt=root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# this is a divider to separate the menu items below from the Debian ones.

title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Fstab here:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fba4ea8e-386b-4a04-bbcd-aede0fe3b5fe /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=A4246DEB246DC142 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=84608e89-530c-40fb-bea6-9dee4de76f87 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I've compared these with another PC I have dual booting (XP on the first partition though) and I don't see anything wrong.

---

### Post by torgrot on 2007-12-16
Could you also run sudo fdisk -l and put the output here.  That is with a lowercase "L".  It looks like you have windows on an extended partition and you can't boot windows from there.  If sda5 is not an extended partition then perhaps you should check out his page for some more help configuring GRUB [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)  It may be a geometry problem.  If WP is on the second partition, and it is not an extended partition then I would have expected it to be sda2 not sda5.

torgrot

---

### Post by uidb4056 on 2007-12-16
Try to change this 

title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

By this

title Microsoft Windows XP Home Edition
root (hd0,4)
savedefault
makeactive
chainloader +1

---

### Post by mikewhatever on 2007-12-16
It says in the fstab your windows is on /dev/sda5, so the above entry (hd0,4) should work.

---

### Post by tjksn on 2007-12-16
Here is the fdisk output.  From what I can tell there is an extended partition - sda2.  I can't get rid of it using the live CD partitioner so I'm going to download GParted and try it that way.  It shows it is the same start and end blocks as sda5 which has Windows on it so I'm hoping it isn't going to destroy that as well.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9266    74429113+  83  Linux
/dev/sda2            9267       18532    74429145    f  W95 Ext'd (LBA)
/dev/sda3   *       18533       19457     7430062+  82  Linux swap / Solaris
/dev/sda5            9267       18532    74429113+   7  HPFS/NTFS

---

### Post by torgrot on 2007-12-16
Hold your horses there.  You have put windows in the extended partition, you can't boot windows from there.  Back up your disk before doing anything else.  You are going to need to move your windows installation to a primary partition not an extended partition in order to boot it.  You can't get rid of sda2 until you get rid of sda5 that is why the live CD partitioner wouldn't delete sda2.

torgrot

---

### Post by tjksn on 2007-12-16
> **torgrot said:**
> Hold your horses there.  You have put windows in the extended partition, you can't boot windows from there.  Back up your disk before doing anything else.  You are going to need to move your windows installation to a primary partition not an extended partition in order to boot it.  You can't get rid of sda2 until you get rid of sda5 that is why the live CD partitioner wouldn't delete sda2.

torgrot

Ok, that makes sense although I don't know how the extended partition got there in the first place.  So, how can I backup the windows partition, get rid of sda5 & 2, make a new primary ntfs, and then restore windows to the new partition?  Is it as simple as copying all the files on the windows partition to my linux part (sda1), deleting the old then creating the new, then copying the windows files to the new partition?

---

### Post by torgrot on 2007-12-16
You are going to need access to a backup program, like ghost or true image.  I don't know what is available for free under linux.  Perhaps someone else has more knowledge about that.  You need to back up sda5 then delete sda5 and sda2.  Create a new primary NTFS partition and use the backup software to restore to the new partition.  

torgrot

---

### Post by perixx on 2007-12-17
Backing up your Windows-partition should work with this tool very well, but you can't simply make a bootable recovery installation with that again, just a 'file-true' backup, from what I see...

[http://www.linux-ntfs.org/doku.php?id=ntfsclone]("http://www.linux-ntfs.org/doku.php?id=ntfsclone") 

Or you use the gparted Live-CD, it should be possible to do a move of a working XP-installation with it...

perixx

---

