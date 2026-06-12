---
title: "Ubuntu 7.04 on external usb hard drive grub error"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Mykle87 on 2007-05-10
I just want to start off by saying this is my first install of Linux so please bare with me. I read a lot of threads to prep me to install Ubuntu on an external hard drive but it seems I ran into a simple problem. I made sure to install GRUB on my external hard drive as to not mess with my current set up. However, some how it was installed to the swap area that I made on that drive. I can use Super Grub Disk to boot into Ubuntu just fine. How do I set up GRUB on my external hard drive? Thanks.

---

### Post by confused57 on 2007-05-10
> **Mykle87 said:**
> I just want to start off by saying this is my first install of Linux so please bare with me. I read a lot of threads to prep me to install Ubuntu on an external hard drive but it seems I ran into a simple problem. I made sure to install GRUB on my external hard drive as to not mess with my current set up. However, some how it was installed to the swap area that I made on that drive. I can use Super Grub Disk to boot into Ubuntu just fine. How do I set up GRUB on my external hard drive? Thanks.
The live cd can be used to install grub to the external mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The Super Grub Disk can also do this.

Before you do this, boot into Ubuntu using SGD, open a terminal(Applications---Accessories---Terminal),enter:
```
sudo fdisk -l
```
the -l is a small "L"

and
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```
you just need to post the boot entries for your /boot/grub/menu.lst

If you can post the output of these 3 commands, someone might be able to give you more specific instructions.

---

### Post by Mykle87 on 2007-05-13
Alright I am so close. Grub now loads from my external hard drive but nothing boots. I get error 17 "Cannot mount partitions" for Ubuntu and XP.

Here is the output of "sudo fdisk -l"
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492706304 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32        7476    59801962+   5  Extended
/dev/sdb5              32        7476    59801931   8e  Linux LVM

```

Here is the output of "gedit /boot/grub/menu.lst"
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
# kopt=root=/dev/mapper/mcolonel--ubuntu--7.04-root ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/mcolonel--ubuntu--7.04-root ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/mcolonel--ubuntu--7.04-root ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

Here is the output of "gedit /boot/grub/device.map"
```

(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb

```

I know that I am so close. I am a bit confused on how to edit menu.lst. hd2 is my external hard drive. That is what I need to work with. Like I said, Ubuntu and XP won't boot with Grub. If someone has the patience to give me a step by step, I would greatly appreciate it. Thanks in advance.

---

### Post by confused57 on 2007-05-13
I'm assuming you used the live cd to install grub to your external drive mbr and that you're getting a grub menu by booting first to your external drive.  If this is the case, in the grub boot menu, highlight your Ubuntu entry, press "e", change root from (hd2,0) to (hd0,0), then press "b" to boot...if it works this change is temporary, but it can be made permanent by editing your /boot/grub/menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```
you can then change all instances of root (hd2,0) to (hd0,0) and you also need to change this line:
# groot=(hd2,0)
to
# groot=(hd0,0)

You'll probably also need to change your device.map to be able to boot Windows from your external drive:
```
gksudo gedit /boot/grub/device.map
```
change it to something like this:
```
(hd0) /dev/sdb
(hd1) /dev/hda
(hd2) /dev/sda
```

Then this entry may boot your Window's partition from grub:
```
title              Windows XP
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by Mykle87 on 2007-05-15
Thank you so much for all the help Confused57. That did the trick. Now everything is set up exactly the way I want it to be. Thanks again :)

---

### Post by confused57 on 2007-05-15
Glad to hear it worked out for you...thanks for the update.

---

