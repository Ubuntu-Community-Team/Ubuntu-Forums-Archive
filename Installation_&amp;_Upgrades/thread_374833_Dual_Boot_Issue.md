---
title: "Dual Boot Issue"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Swoop-LD on 2007-03-03
Greetings,

I am attempting to install Ubuntu and have run into some issues. Actually I got it installed but cannot get it started.

I have two sata drives and 2 IDE drives installed.

Sata1 contains my WinXP.
Sata2 is a new drive currenty partitioned for WinXP
IDE1 has Ubuntu installed on it.
IDE2 is an old Win drive.

I installed Ubuntu to IDE1 after booting from the Live CD. No issues during install. My sata1 still boots to WinXP perfectly when it is selected as first boot drive in the bios.

I switch to the IDE drive in the bios and I get the Grub menu. I can boot to WinXP without any problems. I choose to start Ubuntu, kernel 2.6.17-10-generic (recovery mode) and I get a whole bunch of commands scrolling down.  

Here is the commands:

root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=dev/hdb2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

Ends with:

Done.
Begin:Waiting for root file system.......

After a long wait I get:

Done.
ALERT! /dev/hdb2 does not exist. Dropping to a shell!



Busybox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)


HELP!

-Swoop

---

### Post by Herman on 2007-03-03
Hello Swoop-LD,
From your Ubuntu 'Desktop' Live/Install CD, can you run 'sudo fdisk -lu' please, and post the results here, thanks, ```
sudo fdisk -lu
``` It will also be helpful to see a copy of your menu.lst file and I think that all you will need to do will be to edit that slightly. Here is a link about how to mount your hard disk installed Ubuntu from the Live CD Ubuntu and access that file,                               [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
And possibly also your device.map file could be interesting too, but I think yours will be okay by the sounds of things.

Regards, Herman :)

---

### Post by Swoop-LD on 2007-03-03
Here is my sudo - fdisk.

For clarity here is the breakdown of my drives by size:

15.3 gig is where I installed Ubuntu
20.4 gig is an old Win 98 drive
81.9 gig is my WinXP drive
160.0 gig is new sata drive - just installed and virtually unused.

-Steve



Disk /dev/hda: 15.3 GB, 15382241280 bytes
255 heads, 63 sectors/track, 1870 cylinders, total 30043440 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    18812114     9406026    7  HPFS/NTFS
/dev/hda2   *    18812115    29511404     5349645   83  Linux
/dev/hda3        29511405    30041549      265072+   5  Extended
/dev/hda5        29511468    30041549      265041   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    40001849    20000893+   c  W95 FAT32 (LBA)

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   160071659    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by Swoop-LD on 2007-03-03
OK, Now how do I find and copy the menu.lst file?

-Swoop

---

### Post by confused57 on 2007-03-03
> **Swoop-LD said:**
> OK, Now how do I find and copy the menu.lst file?

-Swoop
Use the live cd, following the link Herman gave you:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

it's really quite easy to follow...

---

### Post by Swoop-LD on 2007-03-03
Hey I am experienced with Windoze.... this Linux thing is all new and not just as easy YET. :confused: 

But here is my menu.lst file - I must be getting the hang of it now.:lolflag: 

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
# kopt=root=UUID=4e0dbb31-54c9-4bee-8848-412b38281bbc ro
# kopt_2_6=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		MS-DOS 5.x/6.x/Win3.1
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

What is next now???

-Swoop

---

### Post by Herman on 2007-03-03
Hello Swoop-LD,
I have analysed your fdisk info and your menu.lst and I think you probably just need to edit your menu.lst file on the lines beginning with the kernel command to have  "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hd_a_2 ro single" 
and not " kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hd_b_2 ro single"
```
Disk /dev/hda: 15.3 GB, 15382241280 bytes______________________________________(hd1)
255 heads, 63 sectors/track, 1870 cylinders, total 30043440 sectors
Units = sectors of 1 * 512 = 512 bytes

Device________Boot________Start________End________Blocks________Id________System
/dev/hda1____________________63___18812114_______9406026_________7_____HPFS/NTFS
[COLOR=DarkRed] /dev/hda2________*_____18812115___29511404_______5349645________83_________Linux_____Ubuntu[/COLOR]
/dev/hda3______________29511405___30041549________265072+________5______Extended
/dev/hda5______________29511468___30041549________265041________82______Linux swap / Solaris

``````
Disk /dev/hdb: 20.4 GB, 20490559488 bytes________________________________________(hd0)
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes

Device________Boot________Start________End________Blocks________Id________System_____Win 98
/dev/hdb1________*___________63___40001849______20000893+____c W95___FAT32 (LBA)_____MS-DOS

``````
Disk /dev/sda: 81.9 GB, 81964302336 bytes__________________________________(hd2)
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes

Device________Boot________Start________End________Blocks________Id________System
/dev/sda1________*___________63__160071659______80035798+________7_____HPFS/NTFS___Windows XP

``````
Disk /dev/sdb: 160.0 GB, 160041885696 bytes_________________________________(hd3)
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

Device________Boot________Start________End________Blocks________Id________System
/dev/sdb1____________________63__312576704_____156288321_________7_____HPFS/NTFS
ubuntu@ubuntu:~$
``````
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hd[COLOR=Red]**a**[/COLOR]2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hd[COLOR=Red]**a**[/COLOR]2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet
boot

``` Try changing it like that and don't forget to save the changes before you close the file. Reboot and see if it's fixed or not.

Regards, Herman :)

---

### Post by bulldog on 2007-03-03
Probably Herman is right,but I think you have the GRUB and Ubuntu on hd0 [hda]
So if Herman's solution isn't working try this one and copy it over your menu.lst.

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4e0dbb31-54c9-4bee-8848-412b38281bbc ro
# kopt_2_6=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title MS-DOS 5.x/6.x/Win3.1
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by Swoop-LD on 2007-03-03
OK.  I tried both solutions.

Neither solution worked.... but I figured it out!

When I had initially installed Ubuntu - my target drive was not the IDE master drive and I got an error (22 I think). I googled a bunch found an answer that said it needed to be the master IDE drive. So I reconfigured my hdd so it was the IDE master. Then it would boot - sort of - and hang up. 

Then I found this forum - posted and tried everything that was offered - without success BUT your help got me around Ubuntu enough to figure it out on my own. 

I went back to WinXP - completely reformatted my target drive and reinstalled Ubuntu on it. Now it was really the IDE master....and voila it worked.

BUT what I did realize is that Herman did give me the correct info - I had booted in the recovery mode - saw all the script - and it finally got to a "root...." prompt and stopped. I thought it had hung up again, got frustrated and did the reinstall. After the reinstall I did the same thing and then sheepishly realized the error. :redface:  If I would have booted normally after I tried what Herman suggested it would have worked perfectly!

When I booted in normal mode instead of recovery mode it worked flawlessly\\:D/ 

Thanks to all for your help.:KS  I am sure I will be here again as I start to dig deeper into Ubuntu!

-Swoop

---

