---
title: "Can't boot into XP after resizing partition w/ gparted"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by polygry on 2007-02-10
Hi. My problem is that I can no longer boot into XP after resizing my NTFS partion to install Ubuntu. I used gparted from a linux rescue disk to resize my NTFS partition from 235GB to 200GB. I used the remaining 35GB to create a linux ext3 partition and a linux swap partition. Since then, whenever I try to boot up XP, it gives me an error message and gives me a number of booting options, including safe mode, normal, etc. But whenever I try to boot using one of those options, it just restarts the computer. The problem, I think, is that XP can't recognize the NTFS partition. When I boot up using the XP CD and go into the Recovery Console, I get the following:

When I type 'dir' at the C:\> prompt, I get 'An error occurred during directory enumeration'
When I type diskpart, I get for existing partition 'c: Partition1 [unknown] 131072 MB (131071 MB free)
When I type chkdsk, I get 'The volume appears to contain one or more unrecoverable problems.

So, with the diskpart command, I get a partition of unknown format with a size of 131072 MB when in fact, it's an NTFS partition with 200GB of space. In Ubuntu however, this partition shows up correctly as being NTFS and I can access all of the files. I have heard that this has something to do with a discrepancy between memory addressing formats of CHS and LBA? Something to the effect that linux can see the NTFS partition because it only uses the LBA filesystem whereas XP uses CHS? I don't have any knowledge in this area so I can't say if this is true or not.

If anyone can share some insight into this and possible suggest a fix ,I'd really appreciate it. Thanks.

---

### Post by mikewhatever on 2007-02-10
Lets try the traditional way first. What's the error message you get when boot to Windows? Can you also post the output of the following commands from the terminal:
```
sudo fdisk -lu
```
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by polygry on 2007-02-11
> **mikewhatever said:**
> 
```
sudo fdisk -lu
```
Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   461370734   230685336    7  HPFS/NTFS
/dev/hda2       461370735   486030509    12329887+  83  Linux
/dev/hda3       486030510   490223474     2096482+   5  Extended
/dev/hda5       486030573   490223474     2096451   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   156296384    78148161    7  HPFS/NTFS

> **mikewhatever said:**
> ```
sudo gedit /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

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
# kopt=root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro

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

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=c3fdc2ef-e2cd-4353-b8a0-695f72d1e25a ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by mikewhatever on 2007-02-11
I don't see any problem in the menu. Let's wait for more advanced user's opinions.

---

### Post by mosiac on 2007-02-26
I have been having the same problem, and searches are kind of coming up short.  Anyone figure anything out about this issue, is the hard drive just ruined and needs to be redone?

---

