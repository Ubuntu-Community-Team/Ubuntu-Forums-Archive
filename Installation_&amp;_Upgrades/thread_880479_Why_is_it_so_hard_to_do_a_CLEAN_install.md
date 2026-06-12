---
title: "Why is it so hard to do a CLEAN install?"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by davidw89 on 2008-08-05
Ubuntu v8.04.1 live cd install. I am booting from CD atm simply because i can't get it working!!

Hi there. I've deleted Windows Vista and i am trying to do a clean install of Linux. I have 4 Hard drive, 1xTB and 3x500GB. I have completely wiped out a 500GB clean and installed using "Guided-use Entire Disk". But when i boot up, GRUB gives me an "Error 17- Cannot mount selected partition". I have tried over and over again with no ideas on how to fix this. I have tried google but have not found a solution yet.

I've posted screenshots..hopefully someone can help me :(

[http://img147.imageshack.us/img147/1576/screenshotoy3.png](http://img147.imageshack.us/img147/1576/screenshotoy3.png)
[http://img337.imageshack.us/img337/7605/screenshot1yn2.png](http://img337.imageshack.us/img337/7605/screenshot1yn2.png)

What do i change here:
[http://img180.imageshack.us/img180/5457/screenshot2kq0.png](http://img180.imageshack.us/img180/5457/screenshot2kq0.png)
I use:
> (hd0) OR > /dev/sdc 
None works!! :(


This has to do with BIOS booting from drive 1 or something..

I am not very good with Linux but am willing to learn. With Windows XP i just do a clean format and it works :/

Anyone help!!

---

### Post by davidw89 on 2008-08-05
I am trying to follow this instruction:
[http://ubuntuforums.org/showpost.php?p=5235963&postcount=2](http://ubuntuforums.org/showpost.php?p=5235963&postcount=2)

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 59572 478512058+ 83 Linux
/dev/sdc2 59573 60801 9871942+ 5 Extended
/dev/sdc5 59573 60801 9871911 82 Linux swap / Solaris

Since i want to boot from sdc1, does this mean i edit it according (hd2,0) where 2=my third drive and 0=first partition?
But problem is that it's already like that and hence is wrong!!

         1. ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f6cacc49-2488-45d3-b42e-283ad453ceca ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

What is the correct root?

---

### Post by davidw89 on 2008-08-05
Here is the menu.lst

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
# kopt=root=UUID=f6cacc49-2488-45d3-b42e-283ad453ceca ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f6cacc49-2488-45d3-b42e-283ad453ceca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f6cacc49-2488-45d3-b42e-283ad453ceca ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by davidw89 on 2008-08-05
All my drives are SATA

---

### Post by trebllaw on 2008-08-05
try to change (hd2,0) to (hd0,0)

this worked for me when booting from an external usb drive.. this might also work for you.. also, set your bios to boot from the hard drive where you installed ubuntu..

hope this helps..

---

### Post by confused57 on 2008-08-05
If you're getting a grub boot menu, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd2,0) to (hd1,0), press "enter", then "b" to boot.  If (hd1,0) doesn't work, try (hd3,0), or even (hd0,0).
This change is temporary, if you find a root designation that works, but you can make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by davidw89 on 2008-08-06
I had to take out my 3 HD, leave the HD i want and then reinstall Ubuntu and now GRUB works and everything is fine! SO word of advice, plug your HDD out and leave one remaining!

---

### Post by AnarchyCow on 2008-08-06
I have this issue when installing all the time.
I have a ATA Master and a SATA (Main)
What happens to me, is that when installing, Ubuntu detects the ATA first and sets it as sda and sets the SATA as sdb. So, when I install, in grub it says to boot to sdb (hd1,1).
But after installing, the system shows the SATA as sda (hd0) and the ATA as sdb (hd1).

Under the "Advanced" button, just make sure you have the ROOT of your first bootable drive selected, not necessarily (hd0) because sometimes the orders can be different between installation and the first boot. I always set mine as the same I'm installing Linux to. If I'm installing Linux to /dev/sdb1 I set it to go to /dev/sdb if I'm installing to /dev/sda1 then I set it to /dev/sda. Sometimes the order just gets messed up.

When booting and getting that error, it means, simply that the line:
```
root        (hd#,#)
```
In the /boot/grub/menu.lst is set incorrectly. In the grub menu itself, you can use the "E" key and edit the line that looks like "root (hd#,#)". More than likely it is the HDD # and not that Partition #. Mine is always set to "root (hd1,1)" and I have to change it to "root (hd0,1), then to test the changes, simply press "enter" (I believe) to confirm the changes to the line, and then when you are back to the page that lists all the lines, press "B" to try to boot. If it doesn't work, don't fear, no changes have been saved. If it does work. Remember..
```
sudo gedit /boot/grub/menu.lst
```
And change the lines in there so that you don't have to deal with it next time.

---

