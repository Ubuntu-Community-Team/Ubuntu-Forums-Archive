---
title: "Grub multiboot after installing Win XP"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by blinton25 on 2007-08-12
Hello,

I have Ubuntu installed on a laptop, and after resizing and creating a new partition using Gpart, proceeded to install WinXP.

XP installed fine, I then followed the instructions at:

[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)

to repair Grub.

After pressing Tab, my partition table looks like:

grub> root (hd0, 
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x82

I then typed:

# root (hd0,o)

and then 

# setup (hd0)

On restarting, I was booting Ubuntu again, but I don't have the option to select Windows.

What do I have to type to have a menu with the option to boot Ubuntu or Linux?

---

### Post by blinton25 on 2007-08-12
Sorry, just to clarify, I typed:

# root (hd0,0)

and not:

# root (hd0,o)

---

### Post by uclalinux on 2007-08-12
Read the following, I know it says it is for gentoo but grub is all the same. The web page is very simple to follow. 

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)

---

### Post by merlinus on 2007-08-12
Post results of:

```

cat /boot/grub/menu.lst
sudo fdisk -l

```

-merlin

---

### Post by blinton25 on 2007-08-12
Sure, I will also read the provided link:

menu.1st:

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
# kopt=root=UUID=ac7218d2-1026-4bfc-b0a2-acf48fe5d09d ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2355    18916506   83  Linux
/dev/hda2   *        2356        4777    19454715    7  HPFS/NTFS
/dev/hda3            4778        4864      698827+   5  Extended
/dev/hda5            4778        4864      698796   82  Linux swap / Solaris

Disk /dev/sda: 128 MB, 128450048 bytes
8 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         979      125263+   6  FAT16

---

### Post by MQMike on 2007-08-12
You don't seem to have a boot entry for Windows:

title Windows 95/98/NT/2000
rootnoverify  (hd0,1)
makeactive
chainloader +1

Place all that just BEFORE the line *** Begin Automagic kernels list

Oops -- EDIT:
rootnoverify (hd0, 1) is what it should be.
(I posted (hd0, 0) at first.)

---

### Post by MQMike on 2007-08-12
You also said:

# root (hd0,0)
and then
# setup (hd0)

To be clear, you didn't type the comment marks (the hash marks), right?

---

### Post by blinton25 on 2007-08-13
Definitely not typing the # signs :)

Thanks a lot, I can now select between the two Operating System. I also disabled hidemenu and increased the timeout to make it more user friendly.

Thanks again.

---

### Post by MQMike on 2007-08-13
You’re welcome – and congratulations on making it go right!
And I agree about hiddenmenu, too.

Just one thing – 
Your default OS is now Windows, thanks to me since we put it at the very beginning (before *** Begin Automagic kernels list).
The line
default=0
controls the default OS that boots if no key is pressed within the timeout.
If instead you want Ubuntu to be the default, just set default=1
(Numbering starts at zero, and numbering counts the “title” lines, so Ubuntu is on title line 1, counting 0 (Windows), then 1.)  I have a feeling you already know all this, but I put it here in case someone else stumbles upon this.

The reason I put Windows in position zero is that lots of people do!  And I assumed you would, too.  Windows is often the default OS for many people.   By putting it in position zero, its number sequence (zero) never changes when you add OSs at the end or when you get a kernel update (which is added at the top of the Automagic list, just below the *** Begin Automagic line).


Again, blinton25, way to go!


How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(aka Qqmike)  The second post discusses editing menu.lst.

---

