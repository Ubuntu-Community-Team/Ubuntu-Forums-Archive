---
title: "Error 22 &amp; Wrong Boot Partition"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by Glueeater on 2008-03-30
Hi, I've recently gone into some craze with installing linux on every PC in my house.

Haha, anyway, I'm trying to get this wokring but I keep getting Error 22.  My results from fdisk -l are:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c7f5c7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27964   224620798+   7  HPFS/NTFS
/dev/sda2   *       27965       30272    18539010   83  Linux
/dev/sda3           30273       30515     1951897+  82  Linux swap / Solaris

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x390a3909

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9963    80027766    7  HPFS/NTFS

```

Now I don't want to the the second NTFS, I want the first NTFS (the larger one to boot).

I've tried editing GRUB but I feel clueless.  Right now, I believe GRUB thinks linux is on (hd1,1) when in fact it is on (hd0,1).

Blah, my post is probably incoherent, but I hope someone can help!  I haven't been on this since Dapper.

---

### Post by Pumalite on 2008-03-30
Boot your Live CD. Mount your partition:
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
Post:
cat /media/sda2/boot/grub/menu.lst

---

### Post by Glueeater on 2008-03-30
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
# kopt=root=UUID=f70556bb-34ea-4fe1-be93-e2e23316fc08 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=f70556bb-34ea-4fe1-be93-e2e23316fc08 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=f70556bb-34ea-4fe1-be93-e2e23316fc08 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I see what I need to edit, but what do I do in the Live CD to do it?  (changing all the hd1's to hd0's)

---

### Post by Pumalite on 2008-03-30
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Change the root line in your kernel to (hd0,1)
You might have problems anyway because of your mix of SATA and IDE:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Glueeater on 2008-03-30
I tried that and it gave me Error 22.

I tried 

```

sudo grub
root (hd0,1)
```

---

### Post by Pumalite on 2008-03-30
I suggest you install your Windows and Ubuntu to the SATA drive and keep the IDE as storage.

---

### Post by Glueeater on 2008-03-30
> **Pumalite said:**
> I suggest you install your Windows and Ubuntu to the SATA drive and keep the IDE as storage.

That's what I am attempting.  Windows is installed on SATA as is Linux.  However, for some reason it keeps thinking the IDE has Windows on it.  I have an edited menu.lst that should work, but I have no idea how to put it onto the drive (I edited with sudo nano after mounting to /media/sda2/)  How can I put the new file on /boot/grub?

My OSes are installed to SATA and the IDE is storage, sorry for not making that clear earlier.

---

### Post by Pumalite on 2008-03-30
Try reinstalling Grub and this time make sure it is to sda:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Glueeater on 2008-03-30
I somehow solved it! Thanks for ALL of your help.  :) Much appreciated.

In the end I believe this was the soltuion:

```

sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2/ /media/sda2
sudo nano /media/sda2/boot/grub/menu.lst

Save after editing
reboot

```

Thanks a lot!

---

### Post by Pumalite on 2008-03-30
You are welcome. Good luck.

---

