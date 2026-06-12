---
title: "Blank Grub Screen--Blank grub menu"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by WildcatWhiz on 2008-02-25
Last night I was installing some the windows wireless drivers for my hp tx1000. Works great, that's another story.

This morning I boot up the computer (I have only Ubuntu, no partition) and instead of taking me to the log-in screen, I get a blank grub screen with "grub>" and a blinking cursor. I've tried reinstalling grub with the stage1, root, set-up command processes, but I keep getting the same thing. I booted from Live CD and I gedit the boot menu.lst and it is completely blank. That makes some sense, because when I try pressing ESC to get to the grub boot menu it doesn't allow me. 

Help! I can't get 'buntu to log-in.

---

### Post by WildcatWhiz on 2008-02-25
Seriously though. I could use some help. I've tried almost everything. I can't pull up the grub boot menu. All that happens when I turn on the computer is I get to a blinking grub command line. HELP!!!

---

### Post by confused57 on 2008-02-25
> **WildcatWhiz said:**
> Seriously though. I could use some help. I've tried almost everything. I can't pull up the grub boot menu. All that happens when I turn on the computer is I get to a blinking grub command line. HELP!!!
Here's an explanation of possible causes:
[http://users.bigpond.net.au/hermanzone/p15.htm#Returns_to_a_Grub__prompt](http://users.bigpond.net.au/hermanzone/p15.htm#Returns_to_a_Grub__prompt)

You may be able to do a direct kernel boot from the grub prompt:
[http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot](http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot).

If you have another computer, you can make a Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by WildcatWhiz on 2008-02-25
[Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename.]

grub>_


That's exactly what I get. The page says that it might be because of editing the menu.lst file, which, I was in the process of doing recently. How might I go about recreating the menu.lst file?  

Thanks so much in advance.

---

### Post by froy02 on 2008-02-25
Please post the contents of your menu.lst file and the result of sudo fdisk -l.

---

### Post by WildcatWhiz on 2008-02-25
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8e7f9af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
[B]
In terms of menu.lst...It was wiped out. I'm running on LiveCD right now and I'm a little confused about something...Why are there two /boot/grub folders? One is under '/' (directory) and one is on my hard drive /media/disk/boot/grub. The one on my hard drive was wiped. I edited it and added the default lines:[/B]

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
# kopt=root=unionfs ro
# kopt_2_6=root=/home/ubuntu/unionfs ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/home/ubuntu/unionfs ro quiet splash

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/home/ubuntu/unionfs ro single

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


**I can get it to get to the grub boot menu now that I edited the menu.lst but I get an error when trying to boot that says:**

Kernal panic--Not syncing unable to mount root fs on unknown-block (0,0) 
[B]
What do I do?[/B]

---

### Post by confused57 on 2008-02-25
Try to change the kernel root line to the partition as it's identified by fdisk -l:
```
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
```

Have you tried mounting your root partition with the live cd?:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

You may be able to chroot into your Ubuntu install & reinstall grub with apt-get.

Added:  Here's how to chroot into your Ubuntu install:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
sudo mount -t proc none /media/ubuntu/proc
sudo mount -o bind /dev /media/ubuntu/dev
sudo chroot /media/ubuntu /bin/bash
```
then you can try reinstalling grub:
```
sudo apt-get install grub
```

I haven't tried it, but I've seen this method in the forum for chrooting from the live cd:
```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt /bin/sh
```

---

### Post by chex_m8 on 2008-02-25
It sounds like you just need to reinstall grub. You can do this with the live cd or with the "super grub disk"

---

### Post by confused57 on 2008-02-25
> **chex_m8 said:**
> It sounds like you just need to reinstall grub. You can do this with the live cd or with the "super grub disk"
Good point, that may be the first thing to try:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by pregister on 2008-02-25
Thats an afirmitive Super  Grub does wonders!:popcorn:

---

