---
title: "Edgy To Feisty dist-upgrade Cant Access tty job control turned off.. Busybox"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by charith on 2008-02-03
Actually ..

I was trying to upgrade from Edgy to Feisty....

First i tried with the update manager... it gave some error like cannot find kubuntu-desktop (i had kubuntu 6.10), so i used the apt-get dist-upgrade method to upgrade...

the whole download process was over and installations all were over.. So, after that i tried to restart the machine..

But when i restarted 
The Kubuntu Screen appears, after which the screen freezes and after 2 mins
i get the error "cant find tty , job control turned off" 
There was a busybox console, it had some commands to it (around 30 Commands) .. of which sudo was not there...

now i cant get into ubuntu at all..
Please find a solution....

My Comp config is
Intel Pentium D Dual Core Processor
Motherboard Intel D102
512 RAM
ATI Radeon 200
160Gb hard disc.
A Floppy Drive and Dvd Writer..

I had Ubuntu 6.06 , i upgraded to 6.10 and then i tried to upgrade to 7.04 , then this happened..

I coudnt install 6.10, it used to freeze in between..
i couldnt directly install 7.04 since the same error "cant find tty: job control turned off" appeared
About 7.10, it was not even detecting in my disc...
 
Since i upgraded i have different kernel versions of it.. but all of them give the same thing.. it gives only busybox console...
if i try to do it through the safe mode, it stops in between and then busybox comes..

I tried to look in other forums.. Each one had the same error but due to different reasons...
But none of them were appropriate bcos some suggested to use some commands which weren't available in the busybox console...

So Please Try to solve this problem at the earliest...

---

### Post by zvacet on 2008-02-03
Look attachment if that is your situation.If it is read [this](https://help.ubuntu.com/community/UsingUUID).

---

### Post by charith on 2008-02-04
According to the links , it means that the UUID might have been changed,...

Since i had my windows partition i could only read my ubuntu files...

So i am posting my menu.list and fstab files i couldn t find any problem..
 Please check whether you can find any errors

**[SIZE="5"]Menu.lst[/SIZE]**

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
default		8

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
# kopt=root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu, kernel 2.6.17-12-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro single
initrd		/boot/initrd.img-2.6.17-12-386
boot

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
boot

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


[SIZE="5"][B]fstab
[/B][/SIZE

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8 -- converted during upgrade to edgy
UUID=0ba2f5e5-8bb4-4586-8b25-4befe5f79017 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=4050CE3C50CE3884 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=F018B01A18AFDDBA /media/sda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=28E0E2BEE0E290FC /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=84D8EEAED8EE9E24 /media/sda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=FA6CF5FD6CF5B48B /media/sda7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda9 -- converted during upgrade to edgy
UUID=f556bdec-11ef-44cd-952f-5ddfb113e3db none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0



I Had My Default OS as XP ....

---

### Post by zvacet on 2008-02-04
Only thing I can think of is to boot from live CD (Edgy) and try to run commands from link.

---

