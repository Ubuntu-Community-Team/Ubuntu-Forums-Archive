---
title: "Installed Gusty dualbooted with xp, now xp is gone!"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by tj1627 on 2007-10-24
In advance I'd like to apologize:  I'm very new to the whole ubuntu scene, so I'm still learning.

I have (had??) a toshiba laptop with XP media center edition on it.  I downloaded the installation cd for Gusty and booted from it.  (Yes I verified the cd after write and again from the main screen on the boot menu).  I proceeded to install Gusty in a dual boot scenario with XP, telling it to size down the xp partition and then install ubuntu alongside it.

The install went off without a hitch.  When prompted to restart into Ubuntu from live cd, I did.  During the restart I saw the GRUB loader and noticed there's no option to get to my xp installation.  When in ubuntu, I tried to access the xp partition (which was labeled something like 53.7 GB Volume) but it said it couldn't mount it and gave me an error.

The data on the xp drive is of extreme importance to me and I hope it isn't lost.  Any help would be much appriciated.

On a side note, I do not know where the recovery disks are for xp, I wish i did.

For reference, the error displayed when trying to mount the drive from ubuntu is:

"Failed to mount '/dev/sda1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware........."

---

### Post by joelmann on 2007-10-24
Same thing happened to me.  All you have to do is edit /boot/grub/menu.lst and add the windows boot again.  Just uncomment the windows segment and it will work.:)

---

### Post by tj1627 on 2007-10-24
i tried this (not sure if it was done correctly) but it didn't work

---

### Post by logos34 on 2007-10-24
run these commands in a terminal and post it:

[B]sudo fdisk -l

cat /boot/grub/menu.lst /etc/fstab[/B]

---

### Post by tj1627 on 2007-10-24
here's the dump from fdisk -l: 

```
isk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x86918691



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1        7012    56323858+   7  HPFS/NTFS

/dev/sda2   *        7013        9610    20868435   83  Linux

/dev/sda3            9611        9729      955867+   5  Extended

/dev/sda5            9611        9729      955836   82  Linux swap / Solaris

```

and here's the dump from cat /boot/grub/menu.lst /etc/fstab:

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

default         0



## timeout sec

# Set a timeout, in SEC seconds, before automatically booting the default entry

# (normally the first entry defined).

timeout         3



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

# title         Windows 95/98/NT/2000

# root          (hd0,0)

# makeactive

# chainloader   +1

#

# title         Linux

# root          (hd0,1)

# kernel        /vmlinuz root=/dev/hda2 ro

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

# kopt=root=UUID=8f18adee-7663-460a-990f-ea5a9847235b ro



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



title           Ubuntu 7.10, kernel 2.6.22-14-generic

root            (hd0,1)

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8f18adee-7663-460a-990f-ea5a9847235b ro quiet splash

initrd          /boot/initrd.img-2.6.22-14-generic

quiet



title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

root            (hd0,1)

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8f18adee-7663-460a-990f-ea5a9847235b ro single

initrd          /boot/initrd.img-2.6.22-14-generic



title           Ubuntu 7.10, memtest86+

root            (hd0,1)

kernel          /boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda2

UUID=8f18adee-7663-460a-990f-ea5a9847235b /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda5

UUID=a9a15d4f-1d4f-4e13-b03f-3e99b71a83b1 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by logos34 on 2007-10-24
Open up menu.lst as root to edit:

**gksudo gedit /boot/grub/menu.lst**

Add windows entry to bottom after 'end debian automagic kernels list':

> title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Change boot flag (*) in fdisk to sda1:

**gksudo gparted**

-->right-click on sda1>manage flags>tick 'boot' box

make sure sda2 boot box is unticked

Get ntfs-config so you can mount ntfs partition read+write:

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29%7C%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29%7C%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

