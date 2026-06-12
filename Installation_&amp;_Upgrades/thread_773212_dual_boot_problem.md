---
title: "dual boot problem"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by zumbix on 2008-04-28
Hi, I'am new to Ubuntu, this is my first post, seeking for help.
I have installed Ubuntu 8.04 in my laptop which used to have 3 partitions, 2 for XP and one for stuff.I installed Ubuntu in what used to be C:. then I realized I can no longer enter to windows in D: because I screwed up the C: partition formating it in ext3.
I did some research, then tried to fix the MBR with the XP recovery console, but no luck, it just got stuck after BIOS Post, so i put Ubuntu live cd and repair grub again, the problem is that i cant lose that win partition. Is there a way that i can copy the D: win xp to to the C: partition , and  fix the MBR and reinstall ubuntu on a secondary partition?( d:)

sorry if its not clear enough I'm a total newbie to ubuntu y linux and  I'm not very good at english hehe
thanks in advance for any help you can give me

---

### Post by zumbix on 2008-04-28
anyone?, if i am no making myself clear, please ask for the info needed, i realy need help, and i want to keep learning ubuntu.

---

### Post by zumbix on 2008-04-28
this is the info in fdisk -l
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97699769

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       12160    97675168+   f  W95 Ext'd (LBA)
/dev/sda5            3237        6424    25607578+   7  HPFS/NTFS
/dev/sda6            6425       12160    46074388+   7  HPFS/NTFS
/dev/sda7               1        3039    24410673   83  Linux
/dev/sda8            3040        3236     1582371   82  Linux swap / Solaris

```
an in menu.lst
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

title Windows 95/98/NT/2000
root (hd0,7)
makeactive
chainloader +1

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
# kopt=root=UUID=19a7d630-4233-4235-a04b-d53691864777 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=19a7d630-4233-4235-a04b-d53691864777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=19a7d630-4233-4235-a04b-d53691864777 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by logos34 on 2008-04-28
I don't think you will be able to copy windows D: to C: and make it work, so forget that.

Try moving the bootable flag using sudo cfdisk or Gparted to sda5 or 6 (whichever is D: partition).  Also try running fixboot on D: partition from the Recovery console. (Maybe the problem was that the boot files were originally on C partition, which got formatted).

Add a windows entry to menu.lst (bottom), using the sample as a guide.

---

### Post by zumbix on 2008-04-28
hi, thanks for the help, i have done what you said, but no luck, grub says error 12, if i try to enter XP

I have a screenshot of gparted to see if you find something wierd, my d: partition is sda5

---

### Post by logos34 on 2008-04-29
Follow the suggestions here:
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

Herman seems to think there's a chance you can copy it to a primary partition and get it to boot. Good luck.

---

