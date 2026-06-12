---
title: "Installed ubuntu, broke XP"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Farajamo on 2008-07-23
So I decided to install Ubuntu 8.04 on my Windows XP box so I could dual boot. All went well, Ubuntu installed.  The problem was, I tried to get back on XP, and all I got was a black screen. Anyone know why? Thanks.

---

### Post by tamoneya on 2008-07-23
Did it immediately go to the blank screen after selecting XP in grub(where you select the OS)?  Can you post the contents of the file /boot/grub/menu.lst as well as the output of running this in terminal(applications->accessories -> terminal)```
sudo fdisk -l
```

---

### Post by Farajamo on 2008-07-23
Result of terminal code:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb76f3cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19875   159645906    7  HPFS/NTFS
/dev/sda2           19876       30401    84550095    5  Extended
/dev/sda5           19876       29967    81063958+  83  Linux
/dev/sda6           29968       30401     3486073+  82  Linux swap / Solaris


Menu.lst:

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
# kopt=root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by tamoneya on 2008-07-23
looks identical to mine when it comes to the windows XP stuff.  You certain that there were no other messages between grub and the blank screen.

---

### Post by Farajamo on 2008-07-23
A word flashes for a hot second... looks like "Loading.." but not 100% sure... It's weird, I can still see the other partition as "163.5 GB Media" and browse through the windows filesystem... but the "Media" part makes me think I did something wrong (Although I don't *think* I did).

---

### Post by tamoneya on 2008-07-23
grub is saying the "loading...".  If that is all you get I think there may be something wrong with the windows boot setup.  Do you have a windows install disc on hand.  There are some utilities on there that you can use to fix the boot loader on windows.  This will kill grub but you can just copy menu.lst before hand and then replace grub by running the ubuntu liveCD or using supergrub.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Farajamo on 2008-07-23
Is the Ubuntu LiveCD the same as the one I used to install Ubuntu? (Sorry, I'm new to Ubuntu)

---

### Post by Farajamo on 2008-07-23
Also, what if I don't have an XP CD on me...

---

### Post by tamoneya on 2008-07-23
yes it is.  

Here are some details on how to use the ubuntu liveCD (installer) to repair or reinstall grub.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

EDIT: if you dont have a windows cd try and borrow one from a friend.  Ive never seen the windows repair tools in any other form than on the install CD.  If anyone knows otherwise I would be glad to see a link.

---

### Post by logos34 on 2008-07-24
> **tamoneya said:**
> There are some utilities on there that you can use to fix the boot loader on windows.  This will kill grub but you can just copy menu.lst before hand and then replace grub by running the ubuntu liveCD or using supergrub.

If you can borrow a copy of the XP install cd the first thing you want to do is error checking on sda1.  

>'r' to enter Recovery console

at the prompt type:

[B]chkdsk /r 

[/B]This might fix it if the ubuntu installer shrank XP partition to make room for linux (the typical scenario).  Normally the check disk is supposed to run automatically on the next boot into windows.

You can also do (from the xp or super grub cd):

**fixboot **

to rewrite the bootsector of sda1.  But if you do '**fixmbr'** this will overwrite grub on the MBR, and you'd have to restore grub to get back into linux.  Although you can try it as a last resort just to see if you can boot windows.

---

### Post by Farajamo on 2008-07-24
Okay, I did the chkdsk /r, the fixboot, and fixmbr... then reinstalled grub.. tried to load windows, and the same exact thing happened.  =/

---

### Post by xen-uno on 2008-07-24
Probably not fatal, but the red text should have been replaced by the blue, instead of appended. Indicates a possible problem during the last kernel update.

## ## End Default Options ##

[color=blue]title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro single
initrd /boot/initrd.img-2.6.24-19-generic[/color]

[color=red]title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=67f1fe57-c908-4df9-bf7a-03f241ffb9c9 ro single
initrd /boot/initrd.img-2.6.24-16-generic[/color]

title Ubuntu 8.04.1, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Farajamo on 2008-07-25
Wait, the text where I pick what operating system? Because for me, that text is all gray.

---

### Post by xen-uno on 2008-07-25
Yours will be gray as is mine at run time. What I was illustrating with the colored text is where your original menu.lst had errors. You may not have them anymore if you re-installed grub. Post your new menu.lst.

---

### Post by Farajamo on 2008-07-25
Well, after I did the "fixmbr" part, I was able to boot into windows fine (which is what I'm using right now).  I'm thinking that maybe Ubuntu just isn't my thing... So does anyone know how I can remove that partition?

---

### Post by Farajamo on 2008-07-25
Err, please?

---

