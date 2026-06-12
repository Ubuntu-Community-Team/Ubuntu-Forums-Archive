---
title: "Grub screwed after several updates"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-03-05
Hey:

Don't know why this happened but after an update and restart (close to the time I updated the linux-headers and kernel files), my grub now is gone and now shows a command line starting with (grub)

What should I do?

---

### Post by nyarnon on 2009-03-05
Live cd repair.

Follow this manual


[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ronacc on 2009-03-05
what resources do you have available ? another install , a live cd ?

---

### Post by cecilpierce on 2009-03-05
you could try to reinstall grub,

grub> find /boot/grub/stage1
      root (hd?,?) "where your install is"
      setup (hd0)
      quit
reboot and see if it works !

---

### Post by dentaku65 on 2009-03-05
> **PRGUY85 said:**
> Hey:

Don't know why this happened but after an update and restart (close to the time I updated the linux-headers and kernel files), my grub now is gone and now shows a command line starting with (grub)

What should I do?

I suggest to burn SuperGrub cd
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
handy swiss army knife for all the stuff regarding Grub

---

### Post by PRGUY85 on 2009-03-05
Reinstall grub from live cd and nothing happened...

---

### Post by cariboo on 2009-03-05
Check out this [howto]("http:///ubuntuforums.org/showthread.php?t=224351"), it goes into details of what @cecilpierce wrote.

Jim

---

### Post by ronacc on 2009-03-05
take a look at your /boot/grub/menu.lst and see if it looks ok .

---

### Post by PRGUY85 on 2009-03-05
> **ronacc said:**
> take a look at your /boot/grub/menu.lst and see if it looks ok .

Did that with live cd.  It is currently empty.

---

### Post by PRGUY85 on 2009-03-05
Can anyone copy/paste the contents of the menu.lst file so I can add it and see if that works?

---

### Post by caryb on 2009-03-05
mine no guarantee's

```

splashimage (hd0,2)/boot/grub/splashimages/KUBUNTU_splashscreen_faded_sky.xpm.gz
default 0
timeout 10


## ## End Default Options ##

title Ubuntu jaunty (development branch), kernel 2.6.28-8-generic
kernel /boot/vmlinuz-2.6.28-8-generic root=UUID=6776401c-a0a2-48b4-8cef-1fbd238d4677 ro quiet splash
initrd /boot/initrd.img-2.6.28-8-generic

title Ubuntu jaunty (development branch), kernel 2.6.28-8-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-8-generic root=UUID=6776401c-a0a2-48b4-8cef-1fbd238d4677 ro  single
initrd /boot/initrd.img-2.6.28-8-generic

title Ubuntu jaunty (development branch), kernel 2.6.28-7-generic
kernel /boot/vmlinuz-2.6.28-7-generic root=UUID=6776401c-a0a2-48b4-8cef-1fbd238d4677 ro quiet splash
initrd /boot/initrd.img-2.6.28-7-generic

title Ubuntu jaunty (development branch), kernel 2.6.28-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-7-generic root=UUID=6776401c-a0a2-48b4-8cef-1fbd238d4677 ro  single
initrd /boot/initrd.img-2.6.28-7-generic

title Ubuntu jaunty (development branch), memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by ronacc on 2009-03-05
heres what it should be for the 2.6.28-8 kernel, see attachment , you will have to change the uuid to match your boot drive ,don't you have a backup menu.lst you can use ?

---

### Post by Darkshade on 2009-03-05
> **PRGUY85 said:**
> Can anyone copy/paste the contents of the menu.lst file so I can add it and see if that works?

Sure, but remember that what works on one system may not work on another. Remember to backup your old file first.

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color green/black white/black

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
# kopt=root=UUID=f2660b44-09cd-473c-bbf9-3f38983a6201 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f2660b44-09cd-473c-bbf9-3f38983a6201

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
# defoptions=vga=769 quiet

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic
uuid		f2660b44-09cd-473c-bbf9-3f38983a6201
kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=f2660b44-09cd-473c-bbf9-3f38983a6201 ro vga=769 quiet 
initrd		/boot/initrd.img-2.6.28-8-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic (recovery mode)
uuid		f2660b44-09cd-473c-bbf9-3f38983a6201
kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=f2660b44-09cd-473c-bbf9-3f38983a6201 ro  single
initrd		/boot/initrd.img-2.6.28-8-generic

title		Ubuntu jaunty (development branch), kernel 2.6.27-7-generic
uuid		f2660b44-09cd-473c-bbf9-3f38983a6201
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2660b44-09cd-473c-bbf9-3f38983a6201 ro vga=769 quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.27-7-generic (recovery mode)
uuid		f2660b44-09cd-473c-bbf9-3f38983a6201
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2660b44-09cd-473c-bbf9-3f38983a6201 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		f2660b44-09cd-473c-bbf9-3f38983a6201
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by ronacc on 2009-03-05
nuts it didn't attach .I had to add the .txt  extension to get it to send just remove it .

---

### Post by renkinjutsu on 2009-03-05
I think if you boot up from a LiveCD, everything you see under / would be of the livesession .. if you want to get into your /boot/grub directory, you'd have to mount your harddrive, and to get your menu.lst, <mount point>/boot/grub/menu.lst

sudo mkdir /media/HD
sudo mount -t ext3 /dev/sda1 /media/HD

change ext3 and sda1 to suit your system


this happened to me also, but i had the "error 24" in grub.. i tried to fix things, nothing worked, even reinstalled grub, fsck concludes that my hd was clean.. i got fed up, so i reinstalled jaunty (clean install), good thing my home directory was in another partition.. phew!

---

### Post by caryb on 2009-03-05
After reading this I have copied my menu list to my home drive:D


Cary


& a usb stick as well!

---

### Post by Darkshade on 2009-03-05
> **caryb said:**
> After reading this I have copied my menu list to my home drive:D


Cary


& a usb stick as well!

Haha I did it too! Except for the USB... might do that too :D

---

### Post by ronacc on 2009-03-05
any time you are running dev software its prudent to keep bu's of critical files like your menu.lst and xorg.conf and also your browser bm's and password file someplace safe , real safe like a cd or write protected usb stick .

---

### Post by PRGUY85 on 2009-03-05
Thanks for the copy paste.  I couldn't get my UUID working on the menu.lst so I just used root (hd0,0) and now I'm back on Jaunty.

Thanks to everyone for the help.

---

### Post by Darkshade on 2009-03-05
> **ronacc said:**
> any time you are running dev software its prudent to keep bu's of critical files like your menu.lst and xorg.conf and also your browser bm's and password file someplace safe , real safe like a cd or write protected usb stick .

Indeed. I had a bit of a hard time setting up my xorg.conf for my dual monitor setup after I forgot to copy my old one before reinstalling. Now I'm keeping backups of everything important on a separate partition to avoid such problems.

---

