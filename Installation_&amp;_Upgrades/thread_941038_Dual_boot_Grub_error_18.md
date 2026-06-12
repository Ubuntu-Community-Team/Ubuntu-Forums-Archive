---
title: "Dual boot Grub error 18"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by Douten on 2008-10-07
I'm having a Grub error 18 trying to dual boot window xp and Ubuntu.

First I installed XP and it worked fine. Then I boot up live-CD and installed it regularly and got the error. So I figure maybe I didn't put the MBR in the hard disc. So I reinstall window again and restart to make sure it worked fine, which it did. I then tried to install Ubuntu again choosing the hard disc for the boot files. When I restarted the same error 18 is still popping up :confused:

Does anyone know why this is? Many thanks.

---

### Post by Pumalite on 2008-10-07
Check this:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
You might need a 200 MB /boot partition at the beginning of your drive.
Post:
sudo fdisk -lu

---

### Post by Douten on 2008-10-07
Thanks for the reply! Here's what I get:
[HTML]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e852e84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    50203124    25101531    7  HPFS/NTFS
/dev/sda2        50203125   390716864   170256870    5  Extended
/dev/sda5        50203188   388467764   169132288+  83  Linux
/dev/sda6       388467828   390716864     1124518+  82  Linux swap / Solaris[/HTML]

---

### Post by Pumalite on 2008-10-07
sudo mkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
Post:
cat /media/sda5/boot/grub/menu.lst

---

### Post by Douten on 2008-10-07
Here's what it displayed:
[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=5aa16309-f1fa-4f55-a09e-aac0c42dcdf5 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5aa16309-f1fa-4f55-a09e-aac0c42dcdf5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5aa16309-f1fa-4f55-a09e-aac0c42dcdf5 ro single
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
[/HTML]

So I don't really know what all this mean, but I'm guessing I installed the Grub in XP boot which I shouldn't have?

---

### Post by caljohnsmith on 2008-10-07
So just to confirm, you are getting the Grub error 18 before you see a Grub menu on start up? How old is your computer, especially your BIOS? Your Ubuntu partition starts at about 25 GB, which for most modern BIOSes that's not a problem; some older BIOSes though can't access anything past 8 GB, so that might apply to you and be the source of your Grub problem. 

Like Pumalite mentioned before, can you make a ~200 MB partition at the beginning of your drive by shrinking your Windows partition at the beginning? You can do it with Ubuntu's partition editor gparted, and then you could make that the /boot partition for Ubuntu. Or another option would be to shrink the beginning of your Windows partition by only 10-20 MB so you can create a really small ~10 MB partition at the front of the drive dedicated to Grub. Personally I would recommend the 200 MB /boot partition, but let me know if you would like to pursue either of those options and I can give more specific directions of how to do it.

---

### Post by Douten on 2008-10-07
Sure! I don't mind how it would work. I know this pc is around the year 1999-2000 so it can't be that old right? But if I have to make another partition for the boot it's fine! I just know how to do it, thanks! :)

---

### Post by caljohnsmith on 2008-10-07
OK, it is always good to first back up any important files in your Windows partition in case something goes wrong, but if you are careful with gparted, you should be fine. Boot your Live CD again, and when you get to the Ubuntu desktop, press ALT + F2 and type:
```
gksudo gparted
```
The thing to remember with gparted is that it doesn't actually do anything until you hit the "apply" button, so that is your only insurance against mistakes. :) 

Anyway, just select the sda1 Windows partition, right-click and choose "resize", and then shrink the beginning of the Windows partition by about 200 MB. Then with that newly created empty space, make a primary partition and format it to ext3 file system. Once you are done, go ahead and install Ubuntu again, but this time use that first partition as the /boot mount point. Once done installing, reboot and let us know what happens. I should mention there is a good chance you will have to do a few minor repairs on your Windows partition to get it fully working again, so I hope you still have your Windows Install CD somewhere because you will most likely need it. Let me know how it goes. :)

---

### Post by Douten on 2008-10-07
Okay! During the installation the last step (under advance) is where I select the partition for the boot file right?

I've backed up everything so it's all good even if I have to re-install windows again and stuff, just as long as I can dual boot.

Thanks :)

---

### Post by caljohnsmith on 2008-10-07
> **Douten said:**
> Okay! During the installation the last step (under advance) is where I select the partition for the boot file right?

I've backed up everything so it's all good even if I have to re-install windows again and stuff, just as long as I can dual boot.

Thanks :)
No, actually it's not the last stage where you click the advanced button; that is for telling Grub which boot sector to install to, which is different than the /boot directory in Ubuntu (easy to get them confused though). When you go through the installer, choose the "manual" partition option, and there you can select your first partition and give it a "/boot" mount point, and also give your sda5 partition a "/" root mount point for the main Ubuntu install. I'm going from memory here, but I think you'll see what I mean when you go through the installer steps. If not let me know.

---

### Post by Douten on 2008-10-07
Ahh.. I can't believe it. After all this work and it decide to.. work! :)
Many thanks guys :3 just another question though if I don't choose which operating system it'll autoload into ubuntu after a period of time right?

---

### Post by caljohnsmith on 2008-10-07
> **Douten said:**
> Ahh.. I can't believe it. After all this work and it decide to.. work! :)
Many thanks guys :3 just another question though if I don't choose which operating system it'll autoload into ubuntu after a period of time right?
Glad it's finally working. :) You can set which OS entry gets loaded by default by changing the "default <number>" line in your menu.lst. You can edit your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Note that Grub's numbering starts with 0, and not 1. That means "default 0" will load the 1st OS entry in Grub's menu when the countdown timer reaches 0, "default 1" will load the 2nd OS entry, etc. You can change the amount of time before Grub counts down with the "timeout <number in seconds>" line. 

So can you boot Windows OK, or is that a problem now?

---

