---
title: "[SOLVED] Lost boot"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by AlanInVancouverBC on 2008-07-11
I dual-boot. After power-up, I have the choice of XP or Ubuntu. I choose Ubuntu. I then get a series of 4 choices (16-19), plus their 4 recovery modes.
Three days ago, I couldn't get past this line in the boot operation:
"ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!"
It actually stops a few lines later with this:
"[18.030690] usb1-2: configuartion #1 chosen from 1 choice"
but I don't think that means anything.

That's when I did the recovery-mode process.

In the normal boot option, I get to: (initramfs) _

I'm guessing this is a consequence of defragging in XP.

I still have the directories: ubuntu/disks/boot/grub and the following files in the grub folder:
menu.lst
menu.lst~
default
menu.lst.backup
device.map

Someone else had a similar problem and was asked to post the menu.lst.
Here is my menu.lst:

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
default         2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		2

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
# kopt=root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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
# defoptions=quiet splash vga=792

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=BAC08358C08319B1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by AlanInVancouverBC on 2008-07-11
I really don't have happy faces in my menu.lst. I don't know how they got there!!!

---

### Post by meindian523 on 2008-07-11
That's because you have 8 and ) next to each other in the menu.lst,and you didn't turn off smilies while posting the menu.lst here.
Coming to topic,unless you did something to Ubuntu's partitions,no error will occur.Defragging in XP cannot cause this error.

EDIT:Unless of course,you installed ext3 drivers for Windows and tried to run Windows' defrag program on the ext3 partition.

---

### Post by AlanInVancouverBC on 2008-07-11
I don't know what ext3 drivers are. But I didn't install any drivers. 

And as a newby to the forums, I didn't read all the options with posting messages here. No more smilies.

Can I reinstall WUBI and still have my preferences available?

---

### Post by meindian523 on 2008-07-11
Are you having a WUBI install [or] a dual boot?These terms are mutually exclusive and do NOT mean the same.

---

### Post by AlanInVancouverBC on 2008-07-21
> **meindian523 said:**
> Are you having a WUBI install [or] a dual boot?These terms are mutually exclusive and do NOT mean the same.

I had XP installed, and then used WUBI to also install Ubuntu. Therefore, on boot, I have the option of either. Thus dual-boot.

---

