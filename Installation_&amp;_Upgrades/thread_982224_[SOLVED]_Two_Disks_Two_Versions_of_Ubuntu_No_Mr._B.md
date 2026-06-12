---
title: "[SOLVED] Two Disks Two Versions of Ubuntu? No Mr. Bill"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2008-11-14
I started with Suse 10.0 when I purchased it several years ago. When they stopped supporting it I looked around for another Distro. After examing several I settled on Ubuntu. I purchased the DVD for HH on Amazon and installed it on sdb. I have been very pleased with it and now I would like to install it on sda (overwriting Suse), and updating it to the newest version  just to see what 10.0 is like. I intend to keep using HH as my production version. I do not want the new install to mess up GRUB. Here is some info about my system:
```

tommy1@tommy1-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      224909      112423+  83  Linux
/dev/sda2          224910     2329424     1052257+  82  Linux swap / Solaris
/dev/sda3         2329425   156280319    76975447+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000abcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   150288074    75144006   83  Linux
/dev/sdb2       150288075   156296384     3004155    5  Extended
/dev/sdb5       150288138   156296384     3004123+  82  Linux swap / Solaris
tommy1@tommy1-desktop:~$ 


```

```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)

grub> 


```

```

tommy1@tommy1-desktop:~$ cat /boot/grub/menu.lst
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
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title           Suse 10.0
root            (hd0,0)
configfile      /boot/grub/menu.lst

tommy1@tommy1-desktop:~$ 

```

---

### Post by Tom Atkins on 2008-11-15
bump

---

### Post by Topsiho on 2008-11-15
So you want to get rid of Suse 10.0 and install HH in it's place. You also want to upgrade to 8.10 (II) to see what it's like?

I suggest you download and burn Intrepid Ibex and install it on sda. Gets you where you want to be in one giant step, using just a little step.

HH (8.04) is an LTS version, which means you get 3 years support (until (where is my calculator) April 2011). II is a normal version, which gets you support during 18 months, and now my calculator is gone. Using an LTS version will leave you with a rather "obsolete" version in it's latter years, however, but being an enterprise version is maybe a little more stable (use HH 8.04.1, for me 8.04 was rather soso, freezing every other moment).

So it is all up to you, I would do it the easy way (20 minutes, and some extra time to download and install the updates, and the applications that you want).

Topsiho
(the added use of my reply is another bump :)  )

---

### Post by Tom Atkins on 2008-11-17
What I am most interested in is guidance on how do the install without messing up my GRUB menu.

---

### Post by Topsiho on 2008-11-17
Hello Tom,

How are things going now? Would be nice if you could let us know. We on the forum learn from such messages too, you know :)

If my answer was quite off the mark, that would mean that I'll learn from your answer that it was....

I wish you success.

Topsiho

---

### Post by Tom Atkins on 2008-11-17
Hi Tophiso,

I have not done anything yet, I was away a couple of days. Your reply was the most practical  way to go but I wanted to go through the install and update route just to see what if any problems I would have. I am mainly concerned with doing the HH install on the disk Suse is on and not being able to boot what is my Production version.

---

### Post by psusi on 2008-11-17
Just install the new system, then edit your menu.lst to put the entries back for booting the second drive.

---

