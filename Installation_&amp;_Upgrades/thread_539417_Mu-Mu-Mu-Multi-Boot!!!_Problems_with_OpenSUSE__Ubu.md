---
title: "Mu-Mu-Mu-Multi-Boot!!! Problems with OpenSUSE | Ubuntu | Vista Setup"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Spam Banjo on 2007-08-31
KK, My new laptop has finaly arived, pre-installed with damn Vista... which I now realy quite like after using it to arange my MP3s! I couldn't work on it though. It's far too paranoid for me! I use Ubuntu at work, so I need that on my machine.

My problem then...


I managed to set up yet another Windows | Ubuntu dual boot no problem... all was well. Then  had the bright idea of installing OpenSUSE. I know it's a great OS, as a close friend of mine uses it, and has done since about OpenSUSE 6.

The probelm came when I installed OpenSUSE. I had no problem using the partitioner to create a custom setup outside the suggested plan, and the installation went well.

The only problem is that Ubuntu has disappeared from my boot menu. The files are still there... everything, so hopefully one of you can help me out here... I know it can't be difficult and I'm sure theres a Linux-Don out there that will know how to fix this in seconds.

I have managed to get Ubuntu back in the list, but I get "Error 17 : Cannot mount partition on boot" when I try to run it.

It's absolutely killing me. Thanks to OpenSUSE handling boot... Grub is there at startup, so I hope it will just be a case of using the right lines to start Ubuntu. I am a real beginer with partitions and multi-boots, etc... but am pretty good with code due to my ASP background, and am very eager to get some serious Linux usage under my belt!

Any help is greatly appreciated

---

### Post by Pumalite on 2007-08-31
Post sudo fdisk -l (small L). Mount Ubuntu's partition and post cat /boot/grub/menu.lst (from Ubuntu). Post cat /boot/grub/menu.lst (fron openSuse)
I assume openSuse owns the Grub.

---

### Post by Spam Banjo on 2007-08-31
This is my Suse menu

> # Modified by YaST2. Last modification on Thu Aug 30 22:39:07 BST 2007
default 0
timeout 8
gfxmenu (hd0,7)/boot/message

title OpenSUSE 10.2 - 2.6.18.8-0.5
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.18.8-0.5-default root=/dev/sda8 vga=0x314 resume=/dev/sda7 splash=silent showopts
    initrd /boot/initrd-2.6.18.8-0.5-default

title Failsafe -- OpenSUSE 10.2 - 2.6.18.8-0.5
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.18.8-0.5-default root=/dev/sda8 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off
    initrd /boot/initrd-2.6.18.8-0.5-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title		Windows Vista
rootnoverify	(hd0,0)
chainloader	(hd0,2)+1


This is the old Ubuntu menu

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1




I assume Suse owns the grub as the boot menu is the pretty blue one, and all ubuntu options are gone.

I tried the fdisk thing but it's not instaled and I've not figured out how to install from the repos yet. I am googling away as we speak!!!

---

### Post by Pumalite on 2007-08-31
It's: 'sudo fdisk -l'

Grab this:

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet

And paste it below openSuse's Failsafe entry. Save and reboot. We might have to erase UUID's and replace them for /devxx, but i don't know yet. Post sudo fdisk -l

---

### Post by Spam Banjo on 2007-08-31
My mistake...

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2              16         277     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         277        6434    49456102    7  HPFS/NTFS
/dev/sda4            6434       14593    65544186+   f  W95 Ext'd (LBA)
/dev/sda5            6434        6696     2103501+  83  Linux
/dev/sda6   *       11263       14449    25599546   83  Linux
/dev/sda7           14450       14593     1156648+  82  Linux swap / Solaris
/dev/sda8            6696        8524    14691411   83  Linux
/dev/sda9            8525       11262    21992953+  83  Linux

Partition table entries are not in disk order


---

### Post by Pumalite on 2007-08-31
Partition 2 does not end on cylinder boundary.

We might have a problem here. Also Ubuntu points to sda7, but that's swap? Suse points to sda8, which is possibly correct.
Make sure you backup Suse's menu.lst before you change it.
cp /boot/grub/menu.lst /boot/grub/menu.lst.back

---

### Post by Spam Banjo on 2007-08-31
I added the ubuntu entries to the suse menu but got nothing on all four.

Same Error as before. 

Gutted.

Not looking good is i really!?!?!?

---

### Post by Spam Banjo on 2007-08-31
> **Pumalite said:**
> Partition 2 does not end on cylinder boundary.

Do you think it could make any difference if I shrink the partition by a few MB from within Vista to try and get rid of this error.

---

### Post by Pumalite on 2007-08-31
In Suse's menu.lst, change Ubuntu's entry from 'root (hd0,6)' to 'root(hd0,5)'
Let's see what happens.

---

### Post by Spam Banjo on 2007-08-31
> **Pumalite said:**
> In Suse's menu.lst, change Ubuntu's entry from 'root (hd0,6)' to 'root(hd0,5)'
Let's see what happens.

Well... This time it's an Error 15... File Not Found.

The screen reads:

> root (hdo,5)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.20-16-generic  root=UUID=c4175046-77e7-49c9-ad6b-cb65992086d9 ro quiet splash
    [Linux-bzImage, setup=0x1c00, size=0x1a88cc]
initrd /boot/initrd.img-2.6.20-16-generic
    [Linux-initrd @ 0x1f951000, 0x69eba0 bytes]
savedefault

Error 15:File not found

Press any key to continue...

:(

---

### Post by Spam Banjo on 2007-08-31
Recovery mode got a little further... actually got to the root terminal

---

### Post by Pumalite on 2007-08-31
Well, I know we are in the right partition now. Why don't you re-install Ubuntu's Grub with this?: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
That would give you a choice of all the OS's to boot.

---

### Post by Spam Banjo on 2007-08-31
> **Pumalite said:**
> Well, I know we are in the right partition now. Why don't you re-install Ubuntu's Grub with this?: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
That would give you a choice of all the OS's to boot.

I followed the guide and got Ubuntu's grub to load... the only problem is I now get the old error again tring to start.

I'm gonna re-set for the Suse grub and see what I can do to find out what file is missing.

have you any idea what the 'savedefault' line does in the ubuntu boot entry?!?!

Should I try removing this or could this be a bit dangerous?

---

### Post by Spam Banjo on 2007-08-31
> **Spam Banjo said:**
> have you any idea what the 'savedefault' line does in the ubuntu boot entry?!?!

Should I try removing this or could this be a bit dangerous?

I did and... Woooooooooooh!!! 


It only worked!! \\:D/

I say worked... I currently have ubuntu on screen, via the OpenSUSE grub. Which is very pretty. I have not clicked around much yet but I am logged in, on my desktop and all seems well.

If anyone knows why I need that 'savedefault' command then please let me know... but I think the command is pointing to the old mount when we had it pointing to (hd0,6). If I could get in and change the grub I suppose I could put the command back

I AM SOOOOO HAPPY!!!

I will get some heavy duty usage in over the next 24 hours and post back here if I get any more related problems.

Thanks so much for your help Pumalite. 
Is there any way of giving you forum-kudos?

---

### Post by Pumalite on 2007-08-31
You are welcome. The kudos are to you for all the hard worked and the courage to implement brilliant but risky ideas. I'm very glad it worked for you.

---

### Post by Spam Banjo on 2007-08-31
> **Pumalite said:**
> You are welcome. The kudos are to you for all the hard worked and the courage to implement brilliant but risky ideas. I'm very glad it worked for you.

I love the Ubuntu community!!! We're awesome!! xXx

---

### Post by Spam Banjo on 2007-09-03
OK... I used it over the weekend and now I have another problem.

Windows is fine... Ubuntu is as awesome as always... But OpenSUSE. Hmmm.

When I boot to Suse it says something about the drive not being mounted. I took it to a friend of mine who's been working with Linux forever, and he did some check & repair thingy... (Sorry, I'm new to Linux and he works very fast, so I didn't catch what he did!) ...that was supposed to fix any errors. It repaired about 12 errors, but still didn't solve the problem. He said he'd have proper look next time I see him, but I prolly won't see him for weeks now.

Multi boot is harder than I thought but I won't stop till I nail it. Any experienced users who wanna flick tips at me, feel free. I'm at a bit of a loss and am having to use Google now as my only option to fix this.

Perhapse I shoud post this in a Suse forum too :KS

---

### Post by Spam Banjo on 2007-09-06
I got the problem sorted.

My freinds brother did it for me, but I kinda picked up on the fact that he booted into text-only from disk, to save mounting the drives. then he ran a check on the hard drive (sorry, didn't catch the command used) that checked the sectors for errors. It found 3 errors and fixed them within seconds.

The whole thing now works perfectly.

The only thing I'm worried about now is that partition that does not end in the right place.

I kinda get the idea the only side effect would be a slight loss of space due to the fact that the partition ends, but the next one does not start straight away.

Hope this thread helps someone. I've learned a lot from this.

---

### Post by ancientt on 2008-04-27
Quick note for others following this thread:

savedefault is a grub command to set the system so that the next time you boot, you will boot into the same OS selection you choose last time.

In other words, if you choose to boot Ubuntu this time, you will boot Ubuntu next time by default. If you choose OpenSuse this time, you will boot OpenSuse next time by default.

This may not be supported by all/unpatched/opensuse versions of grub.

If it works on yours, to use it you should put the 'savedefault' command after each OS selection menu you want to normally use (not failsafe's for example) and set the default entry at the top to use 'saved'.

---

