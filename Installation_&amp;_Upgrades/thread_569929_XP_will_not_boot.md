---
title: "XP will not boot"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by jrcoldren on 2007-10-07
I installed Ubuntu Feisty.  In the installation process I allowed the install to create a second partition for Ubuntu.  After all is done and I reboot and get the selection menu I select 
Windows XP.  The word setup appears on the screen and then the cursor, after that nothing happens   Ubuntu runs fine.  I can see the the windows partition and read the files there in.  But Windows XP will not boot.

Help

Jim

---

### Post by ryanVickers on 2007-10-07
Install the "Gnome Partition Editor"

Run it (System > Administration > Gnome... ) and post a screen shot.

Also, open /boot/grub/menu.lst and post that

---

### Post by jrcoldren on 2007-10-07
I am still trying to figure out how to do a screen capture for the gnome partition 

until then here is the Copy of gedit:

PS..  the path specified on the "gnome partition" for MS windows was /dev/sda1 and not /dev/hda1 as listed below.

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
# kopt=root=UUID=fda54cbe-1e7d-416b-b333-1a05aa661c3b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fda54cbe-1e7d-416b-b333-1a05aa661c3b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fda54cbe-1e7d-416b-b333-1a05aa661c3b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fda54cbe-1e7d-416b-b333-1a05aa661c3b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fda54cbe-1e7d-416b-b333-1a05aa661c3b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

screen shot of gnome partition

---

### Post by ryanVickers on 2007-10-07
well, I can't be sure of the problem until I get a screenshot of the gparted (just open it and hit "printscreen"!), but according to this, windows is the first partition, and linux the second.  I this is true, then everything ***should*** work fine... ...there's nothing wrong with the file!

---

### Post by jrcoldren on 2007-10-07
Got it, Thanks

I hope this works!!

[ATTACH]45603[/ATTACH]

---

### Post by ryanVickers on 2007-10-07
according to the screen shot, there's something wrong with the windows partition - try running "fsck /dev/sda1" in the terminal (make sure it's unmounted though)

also, maybe try setting the boot flag to be on the Linux partition (~!warning!~)

---

### Post by Blindraven on 2007-10-07
When you last rebooted out od Windows, did you restart properly?
If not you need to get back in to Windows and restart normally back in to Linux - its an annoying journaling measure which keeps your **** from getting corrupted - it happens to me all the time.

---

### Post by jrcoldren on 2007-10-07
OK, I ran fsck /dev/sda1 and I made sure that sda1 was unmounted.

this is what I got..
fsck: fsck.ntfs:  not found
fsck: error 2 while executing fsck.ntfs for /dev/sda1.

---

### Post by ryanVickers on 2007-10-07
oh, right, that may not work for ntfs! :p

um, hold on - I'll find you some apps and commands... ;)

Edit:

ok, install:
-ntfs-config

and run:
-ntfs-config (and check off making everything writable)

Note: this won't really help ;)  I"m still looking for the check command...

Edit 2: Well, I don't think there is one, but, hmm...

---

### Post by jrcoldren on 2007-10-07
Ryan,

ran the ntsf-config

standing by

Jim

......................................

Ryan,

This is the first time to boot windows after the installation of Ubuntu and the repartition of the drive.  Would there be some association there?

Jim

---

### Post by ryanVickers on 2007-10-07
oops - double post :)

---

### Post by ryanVickers on 2007-10-07
Ok, burn this as an [ISO]("http://www.hotlinkfiles.com/files/464647_tdey1/CDROM.iso") and boot from it.

Try to "restore grub" to the MBR **and** the ubuntu partition... see if it works *bitting nails*...

---

### Post by jrcoldren on 2007-10-07
I tried to download ISO and got this

Access Denied.

Jim

---

### Post by ryanVickers on 2007-10-07
oh, strange...
try it now - I moved it...

Once you get it - it should be fairly quick because it's only like 4MB ;)

---

### Post by jrcoldren on 2007-10-07
what is the new link?
I used the previous provided the got the same results

---

### Post by ryanVickers on 2007-10-07
:mad:[SIZE=1][COLOR=DimGray](god I hate that site...!)[/COLOR][/SIZE]
try here then: [http://www.mediafire.com/?dv4bdnx3xl8]("http://www.mediafire.com/?dv4bdnx3xl8")

---

### Post by jrcoldren on 2007-10-07
got it

---

### Post by ryanVickers on 2007-10-07
So, everything works now?! :)

---

