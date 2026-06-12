---
title: "Win XP lost:("
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Liliabl on 2008-11-16
I just installed Ubuntu 8.04.1, earlier today and it let me see both Windows XP and Ubuntu in the demo from the live disk.  I think I selected Ubuntu as the only OS by mistake because I can no longer see anything for windows XP.  I used the second guided version, and later read that one replaces one OS for the other >.<  Only Unbuntu is displaying.  I tried to use the Microsoft Windows XP home CD that came with my computer, to get it back, but it is not reading it at all. I tried the recovery CD and it went straight to Ubuntu as well:(

I tried the terminal and the only thing that it gave a response to was the command df -h.  fdisk -l is just blank, waiting for another command.

1. Can anyone help me get XP back so I can have both Please?!?!?!?!??!?

2. In Ubuntu I can't get any audio or video from imeem, or youtube,  
   which is why I wanted to use XP.  Does anyone know what is up with   
   that?  I downloaded all three of the drivers listed.

3. How do I uninstall Ubuntu?  I was thinking that if I took it off and 
   there was no OS then my PC would have to read my reboot disks, I 
   could get XP back, and then I could install Ubuntu again...

4. What happened with all the space I left partitioned for XP?  I know I 
   left 90% to XP and gave 10% to Ubuntu.  


Thanks in advance:)

---

### Post by bulldog on 2008-11-16
Can you post the output of ```
sudo fdisk -lu
``` from a terminal?

---

### Post by Liliabl on 2008-11-16
It asks for a sudo password...is that my Ubuntu password?

---

### Post by Liliabl on 2008-11-16
wow it is!!  here is the reply:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325   271321784   135620730    7  HPFS/NTFS
/dev/sda3       302760990   312496379     4867695   db  CP/M / CTOS / ...
/dev/sda4       271321785   302760989    15719602+   5  Extended
/dev/sda5       271321848   301347269    15012711   83  Linux
/dev/sda6       301347333   302760989      706828+  82  Linux swap / Solaris

Partition table entries are not in disk order
lilia@FreeMangos-desktop:~$

---

### Post by bulldog on 2008-11-16
It seems there's a windows environment on sda2 and a Dell partition on sda1,on sda3 I'm not sure what's there,maybe you know what it means.

To try to start your windows,you'll have to create an entry in your menu.lst.
If there's no damage done to your windows partition it should work.
If you can boot ubuntu,post your menu.lst.
```
cat /boot/grub/menu.lst
``` then we can have a look if there's a windows entry,and if not,we ,make one.:)

---

### Post by Liliabl on 2008-11-16
I will write the windows environment stuff down and check it later...I can't get into windows at all now...But ur advice seems to be working!!!!Here is what I got:
lilia@FreeMangos-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fce7f751-52ac-443c-828c-a245b308fabc ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fce7f751-52ac-443c-828c-a245b308fabc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fce7f751-52ac-443c-828c-a245b308fabc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

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
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

lilia@FreeMangos-desktop:~$

---

### Post by bulldog on 2008-11-16
Don't understand your problem I think.
I see a windows entry in your menu.lst,so it should be in GRUB as well.
In my opinion you can start windows from GRUB,did you try that?
Maybe you have to scroll down a little in GRUB in order to see your windows entry.
If you want to boot windows by default,instead of ubuntu,it can be done by changing a little thing in menu.lst.

---

### Post by Liliabl on 2008-11-16
I see it in what I sent u as well, so thank god it is there!  But I can't get to it.  When I turn on my computer it only lets me select from 3 options of Ubuntu  generic, reboot mode, and something else, but it does not list Windows XP.  Can u please tell me how to start windows from GRUB and maybe that will do it!:)

---

### Post by bulldog on 2008-11-16
Well it should be there,because GRUB reads your menu.lst and let you choose from all the entry's in menu.lst.
Take a closer look at GRUB,is there a scroll-bar at the right side?
If so,use your up and down arrow keys to scroll down.

If not,try to change this part in menu.lst```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0
```
Change the zero into a four.
In order do to so,you need to open your menu.lst as root.
```
gksu gedit /boot/grub/menu.lst
```
Save the file and reboot, and see if GRUB will start your windows,you'll have to wait 10 seconds though.

If that won't work we can reinstall GRUB and see if it will find your menu.lst and your windows entry at all.

---

### Post by Liliabl on 2008-11-17
Ok so I tried the code, changed the number to a 4 and rebooted.  I choose the "e" to edit the command line and somehow it took me to (hd0, 1) and it did testing for windows xp completed 3 out of 3 tests and then took me to Ubuntu.  I rebooted again and it will just take me to (hdo, 4) and nothing appears for XP...I guess we can reinstall the GRUB like u said b4, how do I do that?  Im kinda clueless about it...

---

### Post by caljohnsmith on 2008-11-17
So on start up, you don't see the option to boot either "Dell Utility Partition" or "Windows XP Media Center Edition" at all? How about moving those entries just above the line in your menu.lst that says:
```
### BEGIN AUTOMAGIC KERNELS LIST
```
Reboot, and let me know if you see either entry in your Grub menu. Also, I wouldn't recommend booting the "Dell Utility Partition", because that is your recovery partition; if you boot that and go through all the steps, it will likely erase Ubuntu and restore just Windows to your computer.

---

