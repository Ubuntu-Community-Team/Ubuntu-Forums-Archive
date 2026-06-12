---
title: "Dual Booting 7.10 with Vista on Thinkpad -&gt; Can't boot Vista"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Infinitas on 2008-02-24
I just installed 7.10 on a Thinkpad T61. Lenovo provides a hidden recovery partition to restore Vista if something should go awry. After getting Ubuntu properly installed, I can't get Vista to boot from Grub. Both the recovery partition (sda1) and Vista (sda2) partition appear in Grub along with the Ubuntu partition. However, when I choose to boot either the recovery partition or the Vista partition it boots into the recovery partition. Any advice?

```

cat /boot/grub/menu.lst

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
# kopt=root=UUID=0d0657d7-6ead-4b30-8585-338a1dc8effa ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0d0657d7-6ead-4b30-8585-338a1dc8effa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0d0657d7-6ead-4b30-8585-338a1dc8effa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Infinitas

---

### Post by dstew on 2008-02-24
Please post the output of **sudo fdisk -l**

---

### Post by Infinitas on 2008-02-24
```

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7086dca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         883     7091200   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         884        5229    34896960    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9014       19457    83885760    b  W95 FAT32
Partition 3 does not end on cylinder boundary.
/dev/sda4            5229        9014    30406320    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            5229        5751     4195768+  82  Linux swap / Solaris
/dev/sda6            7057        9014    15724768+  83  Linux
/dev/sda7            5751        7056    10485688+  83  Linux

Partition table entries are not in disk order

```

---

### Post by dstew on 2008-02-24
It seems that your grub menu is set up correctly. It may be that the Vista partition has become unbootable. That is, the fault is on the Vista partition itself. I do not know exactly how to restore it to a booting condition, but I believe there are programs available on the Vista CD. The XP program to use is called fixboot, and I think there is a VIsta equivalent.

By the way, how did you shrink the Vista partition when you installed Ubuntu? Did you use the partitioner in the installer, or the Vista partitioner? Often, the partitioner in the installer has trouble with Vista partitions, and the collective wisdom is to use the Vista partitioner to shrink a Vista partition, if that is necessary.

---

### Post by Infinitas on 2008-02-24
Well, I don't have any media that came with the laptop. They decided that using a recovery partition would be better. If I want the media I have to pay $45 + shipping to get it. I am hoping there is a way to fix it without paying $45. I used gparted to resize the partition. I've used gparted on Vista partitions before with no issues. Surely there is a way to fix this in Linux.

Infinitas

---

### Post by ghost_ryder35 on 2008-02-25
did you defragment the hard drive first????  I have seen this problem many times before if you do not defrag first.  Download [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)  it should get you back up and running in no time.  !!!!

---

### Post by Infinitas on 2008-02-26
Thank you for the info about Super Grub. I'm sure that will come in handy in the future. I gave up and was able to find a way to restore my windows partition only with the restore partition. This problem is now solved.

Infinitas

---

