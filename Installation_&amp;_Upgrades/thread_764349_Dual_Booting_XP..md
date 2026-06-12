---
title: "Dual Booting XP."
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Lodui on 2008-04-23
I'm almost brand new to linux here.I'm trying to dual boot XP and Ubuntu. 

I have both installed on the same harddrive on my laptop. Got both set up. GRUB is on the MBR.

My question is how do I get grub to give me the option of booting into either OS. man grub

Thanks for the help.

---

### Post by tamoneya on 2008-04-23
grub should do this automatically if you install ubuntu after xp.  Post the contents of /boot/grub/menu.lst

---

### Post by Lodui on 2008-04-23
Installed ubuntu first.

Um, what argument do I give the terminal to display that?

Brand new.

---

### Post by tamoneya on 2008-04-23
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Lodui on 2008-04-23
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
# kopt=root=UUID=9942309f-3921-40e2-9950-a9d0b55110e7 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9942309f-3921-40e2-9950-a9d0b55110e7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9942309f-3921-40e2-9950-a9d0b55110e7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9942309f-3921-40e2-9950-a9d0b55110e7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9942309f-3921-40e2-9950-a9d0b55110e7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by tamoneya on 2008-04-23
put a "#" in front of hiddenmenu.

---

### Post by Partyboi2 on 2008-04-23
This will explain how to restore grub if you have installed windows after ubuntu.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Lodui on 2008-04-23
> **tamoneya said:**
> put a "#" in front of hiddenmenu.

Will That make it so I can see the menu automatically?

It still didn't list XP when I pressed esc at boot.

---

### Post by tamoneya on 2008-04-23
This will effectively hit esc for you so it probably wont show XP. Here is a section from my menu.lst```
title		Microsoft Windows XP Professional

root		(hd0,1)

savedefault

makeactive

chainloader	+1
```
This should work for you as well.  Just add it on to the end of the file and change (hd0,1) to the correct harddrive partition.  (hd0,1) is sda2.

---

### Post by Lodui on 2008-04-23
Alright, I think I grasp what that will do.

Although I'm curious about this.

> **tamoneya said:**
> (hd0,1) to the correct harddrive partition.  (hd0,1) is sda2.

First how do I bring up my partition list?


How do I know what the correct partition to replace it with? Whatever my XP partition is I know, but what is that (hd0, 1) stuff? How do I know?

Thanks Tamoneya.

---

### Post by tamoneya on 2008-04-23
post the result of ```
sudo fdisk -l
```Then i will tell you what it should be.

---

### Post by Lodui on 2008-04-23
it's sda3

---

### Post by Lodui on 2008-04-23
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7906    63504913+  83  Linux
/dev/sda2            7907        8028      979965   82  Linux swap / Solaris
/dev/sda3            8029        9728    13655250    7  HPFS/NTFS
lode@lode-laptop:~$

---

### Post by tamoneya on 2008-04-23
(hd0,2)
a = 0
3 = 2 (indexed at 0)

---

### Post by Lodui on 2008-04-23
Alright. I'll give it a go.

---

### Post by Lodui on 2008-04-23
Like a freaking charm. :D

Thanks a lot Tamoneya.

---

