---
title: "[SOLVED] Dual Booting"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by puredude3 on 2008-05-22
Hello im trying to dual boot XP and Ubuntu but i get an error when i set up the xp to load on grub i get an error invalid or unsupported executable.

I have 4 Partitions 2 NTFS and 2 ext3 partitions

Partition1=ext3 (Ubunto)
Partition2=NTFS
Partition3=NTFS (Windows XP)
Partition4=ext3 (Swap)

---

### Post by Pumalite on 2008-05-22
Boot your Live CD and post:
sudo fdisk -l
Post your specs.

---

### Post by puredude3 on 2008-05-22
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00800080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       17969   144327960    f  W95 Ext'd (LBA)
/dev/sda2           17970       23874    47431912+  83  Linux
/dev/sda3   *       23875       30402    52427776    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5               2       17347   139331713+   7  HPFS/NTFS
/dev/sda6           17348       17969     4996183+  82  Linux swap / Solaris

---

### Post by puredude3 on 2008-05-22
Also booting to ubunto isnt the problem its it wont boot to xp

---

### Post by Pumalite on 2008-05-22
Edit menu.lst
Add:
title Windows
root (hd0,2)
chainload +1

---

### Post by meierfra. on 2008-05-22
Pumalite meant to say

title Windows
root (hd0,2)
chainload[COLOR="Red"]er[/COLOR] +1

---

### Post by Pumalite on 2008-05-22
Oops!

---

### Post by puredude3 on 2008-05-22
that boots to ubunto

---

### Post by meierfra. on 2008-05-22
Does it directly boot Ubuntu, or does  it go to the grub menu?

---

### Post by puredude3 on 2008-05-22
when im in the grub menu and click windows xp it boots to ubunto

---

### Post by meierfra. on 2008-05-22
Post your menu.lst.

---

### Post by puredude3 on 2008-05-22
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=5db727b3-018a-485a-99ee-0b42568b6131 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5db727b3-018a-485a-99ee-0b42568b6131 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5db727b3-018a-485a-99ee-0b42568b6131 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,2)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2008-05-22
Get Super Grub and see if you can boot Windows:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by meierfra. on 2008-05-22
Supergrub is always a good idea, but I doubt that it will work. But  
 give it a try.

 It looks like you installed grub  to /dev/sda2 and overwrote the windows boot sector. So if supergrub does not work, I suggest to boot from a Windows CD and run "fixboot" from the repair console. If you don't have a Windows CD I can give you instruction how use "testdisk" instead.


Also you need to edit your menu.lst so that the Grub menu appears at boot up:

Change

"timeout 3" to "timeout 10"

and

"hiddenmenu" to "#hiddenmenu"

---

### Post by puredude3 on 2008-05-23
Thanks man what you said worked.:guitar:

---

