---
title: "Black Screen with Blinking Cursor after CD install"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by thallium205 on 2007-04-21
After installing UBUNTU AMD64 from the CD to my blank harddrive, after I restart the computer as I am advised, it comes up in a DOS looking screen with only a blinking white "-" on a black screen.  The computer just sits there and nothing happens. I have been having many problems with this Ubuntu, and I really want to try this out!  What is going on and how do I fix it!
Help!:mad:

---

### Post by jpeddicord on 2007-04-22
Does anything else show up before it gets to the blank screen? Something to the effect of "Grub is loading"?

---

### Post by ld50 on 2007-04-23
I"m having this same issue does anyone know the cause/solution????

---

### Post by aurimrv on 2007-04-28
> **thallium205 said:**
> After installing UBUNTU AMD64 from the CD to my blank harddrive, after I restart the computer as I am advised, it comes up in a DOS looking screen with only a blinking white "-" on a black screen.  The computer just sits there and nothing happens. I have been having many problems with this Ubuntu, and I really want to try this out!  What is going on and how do I fix it!
Help!:mad:

I have exactly this same problem... Please, any one can help with this. I already installed/unistalled the system several times on differend disk partitions and nothing happens.

---

### Post by tootlet on 2007-04-28
Try Ctrl-Alt-Backspace. This should kill the Xserver and bring your to a prompt. Then you are going to have to cd to /etc/X11/xorg.conf. Sudo to vi or emacs and edit the file. You can get hints as to what it should read by booting the LiveCD then using gedit to open /etc/X11/xorg.conf. What is happening is either the automatic setting for your monitor is not supported or the driver for your video card hasn't been loaded. Took me some wrangling to get it up. Good luck!

---

### Post by NilsE on 2007-04-28
If you get nothing but this after the BIOS screen and especially if you don't see the grub menu it simply means there is no Master Boot Record to trigger the boot.

At the end of the install from the LiveCD did you get the message to continue with the LiveCD or boot to the new install?  If not it generally means the grub install failed.  You can try to use GRUB from the liveCD to fix it, edit the /boot/grub/menu.lst and see what it looks like or start the install over again and make sure you get through the partition and format section of the install and the grub portion.

Also, reboot from the LiveCD and check to see if the install went well.  In other words look to see if there is anything visible on the hard drive. 

A proper one OS menu should look something like this (drive letters and UUID's will definitely be different)

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
timeout		1

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
# kopt=root=UUID=640a2e9d-8eac-41d5-88a0-2a97984ab369 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=640a2e9d-8eac-41d5-88a0-2a97984ab369 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=640a2e9d-8eac-41d5-88a0-2a97984ab369 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

