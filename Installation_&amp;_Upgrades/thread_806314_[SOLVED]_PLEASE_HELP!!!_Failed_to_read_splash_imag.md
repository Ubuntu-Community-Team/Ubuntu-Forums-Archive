---
title: "[SOLVED] PLEASE HELP!!! Failed to read splash image"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by philidox on 2008-05-24
I'm trying to dual boot my computer.  I'm going from Ubuntu 8.04 to Ubuntu8.04+WindowXp.  I was doing just find and this stupid error came up.  Failed to read splash image (hd1,0)/boot/grub/splashimages/Ubuntusplash.xpm.gz)  Press any key to continue...

After that it just reboots and I'm back in the same crap I was before.  THIS IS DRIVING ME NUTS.  I've tried using the live cd to edit the /boot/grub/menu.lst file but no luck.  I traced the file it says it cannot read and there is nothing wrong with it.  Its not corrupt and the pathway is right on.  Can someone please tell me how to fix this issue.  I cannot boot to anything! I went to this thread and the at the end the guys says thanks but doesnt say how he fix it.  I HATE THAT.  [http://ubuntuforums.org/archive/index.php/t-212478.html](http://ubuntuforums.org/archive/index.php/t-212478.html).  Any suggestion would help a lot.

---

### Post by Partyboi2 on 2008-05-24
Have you tried to reinstall grub with the live cd? [[COLOR=Blue]This link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") will show you how.

---

### Post by Jose Catre-Vandis on 2008-05-24
Agree with Partyboi2, but also

If you have gone through your dual installation, just also check your partition numbers haven't changed, that is that your image and kernel are still at (hd0,1)

Not quite sure why you can't edit the /boot/grub/menu.lst? Did you sudo before you opened it up?

---

### Post by philidox on 2008-05-25
I tried reinstalling the grub and no luck.  I also checked to ensure the splash screen xpm.gz location was correct and not corrupted.  Man this really has me stumped!  Here is a copy of my menu.lst file.  I've narrowed the issue down to this.  When I try to reinstall the grub all I see is (hd0,0), my harddrive is located at (hd1,0).  No matter how  I  mount the the hard drive via gui or cli I cannot get the live cd can only see hd0,0.  

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd1,0)/boot/grub/splashimages/Ubuntusplash.xpm.gz

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
# kopt=root=UUID=cc6f3fd8-4c96-471e-8024-1f98f6d6d8d9 ro

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
# defoptions=splash vga=795

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=cc6f3fd8-4c96-471e-8024-1f98f6d6d8d9 ro splash vga=795
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=cc6f3fd8-4c96-471e-8024-1f98f6d6d8d9 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cc6f3fd8-4c96-471e-8024-1f98f6d6d8d9 ro splash vga=795
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cc6f3fd8-4c96-471e-8024-1f98f6d6d8d9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Jose Catre-Vandis on 2008-05-25
You have two hard drives installed yes? Your plan is for XP on (hd0,0) and Ubuntu on (hd1,0)?

Where is grub installed (hd0) or (hd1)?

---

### Post by PmDematagoda on 2008-05-25
Really saying, why on earth didn't you try to nip the problem in the root, which is the splash image.

Here is the entry to be removed:-
```
splashimage=(hd1,0)/boot/grub/splashimages/Ubuntusplash.xpm.gz
```
Just remove the entry(a working GRUB matters more than a broken one), and then see if that solves the problem.

---

### Post by philidox on 2008-05-25
I fix the issue.  I had unplugged my other hard drives during the installation of xp.  All I did is just reconnect my other hard drive and it worked again.  I can only assume that some of the neccessary boot files were on the other hard drives.

---

### Post by Jose Catre-Vandis on 2008-05-25
Gotcha :)

---

### Post by oakberry on 2009-05-30
I've got the answer -- finally!!

I had the same problem with the splash image not being read.  I tried reducing the color depth, gZipping with external tools, you name it - nothing worked.

Then I found out that GRUB is just really particular about what format the splash files are in.  If you use the CONVERT command, you can take any old PNG file and make it work as a splash.

Try this:

1) make a 640 x 480 splash screen of your choice -- try to keep your graphics in the middle so they don't get overwritten by the loader text.

2) save this image as a PNG -- for this example, let's call it "splash.png"

3) copy it to /BOOT/GRUB

4) convert it and gZip it all at once...

```
convert -resize 640x480 -colors 14 splash.png splash.xpm && gzip splash.xpm
```* note - if your original PNG is already 640x480 it won't get all jaggy when convert does the resize.

That's it!  reboot and watch the magic!

---

