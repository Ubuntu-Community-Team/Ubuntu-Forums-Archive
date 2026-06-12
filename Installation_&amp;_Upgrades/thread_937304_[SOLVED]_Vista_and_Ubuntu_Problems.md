---
title: "[SOLVED] Vista and Ubuntu Problems"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by latestarter on 2008-10-03
New to ubuntu which I like, but not got off to a good start.
Tried to load ubuntu as dual boot but got into difficulties and ended up with inability to boot Vista and no ubuntu. Then loaded ubuntu as complete installation and have been busy adding data etc.
Decided to have a go at booting vista again then lost the ability to boot ubuntu so decided to re-install ubunto.
When loaded I noticed in the Boot selection box in start up the original ubunto OS was still there and all the data etc (sigh of relief).
So now, how do I uninstall the last ubuntu installation or how can I make the original version the one that boots up first (I think I will give up on vista for now).

copy from sudo: fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         181     1453851    7  HPFS/NTFS
/dev/sda2   *       18310       18704     3166016    7  HPFS/NTFS
/dev/sda3           19255       19458     1626112    7  HPFS/NTFS
/dev/sda4             182       18309   145613160    5  Extended
/dev/sda5             182        1036     6867756   83  Linux
/dev/sda6           17569       18309     5952051   82  Linux swap / Solaris
/dev/sda7            1037       16891   127355256   83  Linux
/dev/sda8           16892       17568     5437971   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-10-03
It looks like your two Ubuntu installs are on sda5 and sda7. So go ahead and boot into your new Ubuntu, and open a terminal, and do:
```
mount | grep " / " |  awk '{print $1}'
```
That will tell you which linux partition you have booted into, either sda5 or sda7 (let me know which one :)). If you are in sda7 (my guess), then mount sda5 with:
```
sudo mount /dev/sda5 /mnt

```
Or replace sda5 with sda7 above if you are actually in sda5. Next post the output of:
```
cat /mnt/boot/grub/menu.lst
cat /boot/grub/menu.lst
```
Also, please clarify: are you able to boot into your old Ubuntu from the Grub menu you get on start up now?

---

### Post by latestarter on 2008-10-03
Thanks for your help, you were right, sda7 was the new loaded OS, both OS are now visible in start up but with the sda7 at the top of the list. Is there a way of getting the sda5 OS to the top to auto open if no other selection is made?

---

### Post by caljohnsmith on 2008-10-03
> **latestarter said:**
> Thanks for your help, you were right, sda7 was the new loaded OS, both OS are now visible in start up but with the sda7 at the top of the list. Is there a way of getting the sda5 OS to the top to auto open if no other selection is made?
Sure, you can put the Ubuntu on sda5 at the top of Grub's menu, but you said in your first post that you wanted to uninstall your newest Ubuntu install (sda7); so which do you want to do? Either way, you'll need to at least post:
```
cat /boot/grub/menu.lst
```
While you are in sda7 so I can see your Grub's menu.lst.

---

### Post by latestarter on 2008-10-03
Your right, I would prefer to uninstall sda7 if possible.

cat /boot/grub/menu.lst
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
# kopt=root=UUID=15ab6725-6d7f-4130-9c91-e30efd6d9eec ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=15ab6725-6d7f-4130-9c91-e30efd6d9eec ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=15ab6725-6d7f-4130-9c91-e30efd6d9eec ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by caljohnsmith on 2008-10-03
OK, let's see if your menu.lst in the sda5 partition is usable:
```
mount /dev/sda5 /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output from above, and from that we can first make sure your sda5's menu.lst is OK before we reinstall Grub to tell Grub to use sda5 instead of sda7 on start up.

---

### Post by latestarter on 2008-10-03
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
# kopt=root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro single
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
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-10-03
Great, your menu.lst from sda5 looks like it should work fine. So now we need to reconfigure Grub so that Grub will look on your sda5 partition for its menu.lst and all its other system files:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Then reboot, and you should see the menu.lst from the sda5 partition, so you will only have options to boot into your old Ubuntu and Windows Vista. Once you boot into Ubuntu, make sure you are in sda5 with:
```
mount | grep " / " |  awk '{print $1}'

```
If that shows sda5, then you are all clear to get rid of sda7 and sda8. To do that, boot your Live CD, open gparted:
```
gksudo gparted
```
And go ahead and delete sda7 and sda8. Then if you want you can make a new logical partition with that space and use that for file storage or whatever you want. I would use NTFS or FAT32 as the file system so that the new partition will be easily accessible in both Windows and Ubuntu. Let me know how it goes or if you run into problems.

---

### Post by latestarter on 2008-10-03
All gone well up to booting live CD, but not getting a response from gksudo gparted. I have loaded CD whilst in booted sda5 and entering the code in the terminal in the same.

---

### Post by latestarter on 2008-10-04
Tried again and got into gparted. Tried to delete but not allowed. 
Message on screen
Unable to delete /dev/sda7!
Please unmount any logical partitions having a number higher than 7

On terminal. 

ubuntu@ubuntu:~$ gksudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.

---

### Post by caljohnsmith on 2008-10-04
> **latestarter said:**
> I have loaded CD whilst in booted sda5 and entering the code in the terminal in the same.
So did you boot into the Live CD on start up and not boot it somehow while you are in sda5? You want to boot the Live CD on start up, and once you are in Ubuntu on the CD, open a terminal (applications > accessories > terminal), and then do:
```
gksudo gparted
```
Most likely your Live CD will try to use one of the swap partitions sda6 or sda8, so just right-click those partitions in gparted and choose "swapoff". Then you should be able to delete sda7 and sda8 I think.

---

### Post by JMall on 2008-10-04
I'm new to Ubuntu but I think I might be in the wrong place. I read the thread above and I could not follow what was going on.

Wasn't this suppose to be a Brittney Spears forum?

---

### Post by latestarter on 2008-10-04
Success, swapoff worked, I have deleted sda7 and 8 and re-booted twice to ensure OK.
Many thanks for your help and patience, I have also learned some new terminology and how to get around some bits of the operating system. Thanks again.

---

### Post by caljohnsmith on 2008-10-04
That's great news, latestarter, and I'm glad I could help out. Cheers and have fun. :)

---

