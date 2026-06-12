---
title: "Dual-booting on multiple drives"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by tiredtired on 2008-02-03
Well, I have a primary hard drive (SATA) with Windows XP, and an IDE drive that I decided to install Ubuntu on and dual boot.

I installed Ubuntu, formatted and partitioned the secondary drive, and the installation went smoothly. I rebooted hoping to see a boot menu with my two OS's, and... it boots straight to XP without a boot menu. Okay, it's apparently not that easy.

What do I do?

For my board there is unfortunately no BIOS boot order option that allows me to boot one drive before the other. So I have no way to get to my Ubuntu install, and have just been trying to see what I can do via the liveCD.

I've searched and tried out several methods already, with no success, so hopefully someone here can help.  I've mainly only been able to find obscure guides that are very technical. I've never used Ubuntu or any kind of Linux before. I understand what grub is but have no idea where the installer has put it or how to find out.

The goal is to have a boot menu where I can choose one or the other.. is there a simple guide or process somewhere? Or some kind of app that just sets it up automatically? Preferably doable from Windows, as my Ubuntu install is inaccessible (tried WINGRUB, no luck).

---

### Post by Pumalite on 2008-02-03
Try Super Grub to boot Ubuntu: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by tiredtired on 2008-02-03
> **Pumalite said:**
> Try Super Grub to boot Ubuntu: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Hi,

I  tried it, but to no avail.

Can it be used to set things up so I can dual-boot without it? If so I'm not sure I understood how.

In any case, I thought I'd at least try booting Ubuntu using the disc.. but that's not possible either. I get Error 17 when I try.

Out of interest, I get errors if I try to boot windows from there too.

---

### Post by Pumalite on 2008-02-03
Your best option is to make room for Ubuntu in your SATA drive, keep that as Master and use your IDE drive for Data or a separate /home.

---

### Post by tiredtired on 2008-02-03
Too bad the IDE drive was full of data and I formatted the lot just so I could use Ubuntu on it - bit late to change my mind now. :(

Installing on a second drive seemed the clear, logical choice, and I expected it to be the easiest as well... so must make it worth it, and get Ubuntu settled into its intended home. 

Surely for such a simple and presumably common task there is more than just theories, but something documented somewhere that actually says "Here's *the way* to do it.. blam, done"? If there's not, then I'm amazed and think there certainly well should be. I'm already amazed enough that it was not an option automatically presented and set up during the Ubuntu installation process.

In any case, it certainly seems possible to do, it's just a matter of how. Is there a way to get past Error 17? It's interesting that booting *anything* from the supergrub disk was impossible - even windows. Regardless of the mode. I'm not sure what this is indicative of, but it seems suggestive.

---

### Post by Herman on 2008-02-03
:) Hello tiredtired,
The easiest way to get your computer to boot and get past grub error 17 for you would be to go into your BIOS and switch the [hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") around so your PATA (IDE) hard disk will be seen as your number1 hard disk in your BIOS.

That should fix it.

But you said " For my board there is unfortunately no BIOS boot order option that allows me to boot one drive before the other."

Please check again and see if there's a way to change the_ hard disk boot priority_, (not the 'boot order', but the 'hard disk boot priority', (or whatever it's called in your BIOS).

Otherwise you'll probably have to re-install GRUB to MBR in your PATA (IDE) hard drive and then edit your /boot/grub/menu.lst file to suit, which will be more work for you. 
You will probably need to [                                  Mount your Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") and rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000].
Or else, boot your Ubuntu with Super Grub DIsk. You should be able to boot it with Super Grub DIsk if you use the advanced menu and choose a direct boot.
Another way to use Super Grub DIsk is to press your 'c' key and go into [/COLOR][/COLOR][GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")[COLOR=#666666][COLOR=#000000] and do this, [/COLOR][/COLOR][**Direct (kernel) Boot**]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").
Then you'll be able to fix it from withoin Ubuntu, you'll probably need help, because you'll have to install GRUB to (hd1) and turn a few of your GRUB settings upside down, but it won't be too hard. We'll cross that bridge when we have to.

As I said, the easiest way will be to just switch you hard disk boot priority in your BIOS. 
What brand of mother board do you have or what type of BIOS do you have? [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information")

Regards, Herman :)

---

### Post by Herman on 2008-02-03
> Surely for such a simple and presumably common task there is more than just theories, but something documented somewhere that actually says "Here's *the way* to do it.. blam, done"? If there's not, then I'm amazed and think there certainly well should be. I'm already amazed enough that it was not an option automatically presented and set up during the Ubuntu installation process. I tried very hard to replicate your problem in this thread,                                                                                                                                                [ [IMG]http://ubuntuforums.org/images/uf/misc/paperclip.gif[/IMG]]("http://ubuntuforums.org/subscription.php#")                                                                                                                                          [Grub error 17]("http://ubuntuforums.org/showthread.php?t=442945")([IMG]http://ubuntuforums.org/images/uf/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=442945") [2]("http://ubuntuforums.org/showthread.php?t=442945&page=2") [3]("http://ubuntuforums.org/showthread.php?t=442945&page=3") ... [Last Page]("http://ubuntuforums.org/showthread.php?t=442945&page=17")) but I wasn't able to get my computer to produce that error.
The outcome of that thread was, we think the simplest solution is to turn your hard disk boot priority in your BOIS if you can and than has worked for several people already.

Other people who know more than me have tried too. Apparently (as far as progamming goes), it is only possible to solve the GRUB/Linux PATA/SATA BIOS hard drive priority issue for the majority of machines and not for all computers. They could change some programs to suit computers with BIOSes that prioritize it the way yours does, but that would put the rest of them out whose computers get it right now.
Maybe if they had a big convention and got all the motherboard (BIOS) manufacturers to agree on how to standardize their BIOSes then things would be easier, but I won't be holding my breath waiting for that to happen.

At the moment GRUB is the only boot manager I know of that is capable of setting itself up automatically at all, and it works well for the majority of computers. 
I'm sorry to read of your problems but hopefully they should be relatively simple to solve.

There are a couple of well know threads here in Ubuntu Web Forums on dual booting with two hard drives, those may be of some help. 
                                                                                                                                                                                                                                                                              [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902") 

[CENTER][**Trying to Dual Boot, using two HD's**]("http://www.ubuntuforums.org/showthread.php?t=120994")
[LEFT]
Regards, Herman :)
[/LEFT]

[RIGHT][LEFT]
[/RIGHT][/LEFT]
                                                                                                                                                                                                   [/CENTER]

---

### Post by pieisgood4589 on 2008-02-03
LILO, anyone?

---

### Post by Herman on 2008-02-03
[LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html")

---

### Post by tiredtired on 2008-02-03
> **Herman said:**
> :) Hello tiredtired,
The easiest way to get your computer to boot and get past grub error 17 for you would be to go into your BIOS and switch the [hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") around so your PATA (IDE) hard disk will be seen as your number1 hard disk in your BIOS.

That should fix it.

But you said " For my board there is unfortunately no BIOS boot order option that allows me to boot one drive before the other."

Please check again and see if there's a way to change the_ hard disk boot priority_, (not the 'boot order', but the 'hard disk boot priority', (or whatever it's called in your BIOS).

Otherwise you'll probably have to re-install GRUB to MBR in your PATA (IDE) hard drive and then edit your /boot/grub/menu.lst file to suit, which will be more work for you. 
You will probably need to [                                  Mount your Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") and rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000].
Or else, boot your Ubuntu with Super Grub DIsk. You should be able to boot it with Super Grub DIsk if you use the advanced menu and choose a direct boot.
Another way to use Super Grub DIsk is to press your 'c' key and go into [/COLOR][/COLOR][GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")[COLOR=#666666][COLOR=#000000] and do this, [/COLOR][/COLOR][**Direct (kernel) Boot**]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").
Then you'll be able to fix it from withoin Ubuntu, you'll probably need help, because you'll have to install GRUB to (hd1) and turn a few of your GRUB settings upside down, but it won't be too hard. We'll cross that bridge when we have to.

As I said, the easiest way will be to just switch you hard disk boot priority in your BIOS. 
What brand of mother board do you have or what type of BIOS do you have? [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information")

Regards, Herman :)

Hi, thanks for all the help.

There is no boot order priority option for multiple tries in my BIOS unfortunately - there is only the usual options of 'Hard Disk', 'Floppy' etc. I just took another look to be sure, no luck.

With SuperGrub disk I already tried a direct boot through the advanced menu (and for the sake of it, every other possible way). I always get error 17. Actually, once in the SuperGrub menu, there is no possible way to successfully boot ANY OS, Ubuntu or XP, such that the only way out of it is to switch the computer off. :(

Hard disk boot priority and SuperGrub seemed to be the easiest options, so it looks like I need to do something trickier (which is where I fall down, because I'm not familiar with a lot of the linux techspeak).

Thanks for the link ('Dualboot Two Hard Drives' thread), but actually I'd already read that thread and tried every one of those options already (and tried various other things I found around online), before making a post. Forum etiquette and all. :) I didn't have any luck, although admittedly for some of them it was likely because I just couldn't follow it.

---

### Post by Herman on 2008-02-03
Okay then, please post here the outputs from 'sudo fdisk -lu',```
 sudo fdisk -lu
```You will need to use the Ubuntu LiveCD to run these commands from, the 'sudo fdisk -lu' command is fairly striaght forward.

For the 'gksudo gedit /boot/grub/menu.lst' file, you will find that a little more complicated from the LiveCD. The mistake a lot of people make is to type the command like that as if they would be getting the /boot/grub/menu.lst from the LiveCD and they end up with an empty file, and scratch their heads in puzzlement.
What you will need to do is 'mount' your hard disk installed Ubuntu file system in the Live CD first, then get the menu.lst file from /boot/grub in the hard disk.
```
sudo mkdir /media/ubuntu
``````
sudo mount -t ext3 /dev/hda1 /media/ubuntu
``````
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```Here's a link to explain what I'm trying to tell you in case you need to refer to it, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000]. 
If you can do that I'll 'doctor' your /boot/grub/menu.lst file a little for you and send you back an ammended copy, and explain to you the steps to install GRUB to MBR in your first hard disk. That should get it working properly for you.

Regards, Herman :)
[/COLOR][/COLOR]

---

### Post by tiredtired on 2008-02-04
Thank you for your help. :)

Here is the data:

 sudo fdisk -lu

> Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   149838254    74919096   83  Linux
/dev/hdc2       149838255   156296384     3229065    5  Extended
/dev/hdc5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

menu.1st
> 
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
# kopt=root=UUID=64b0b219-0478-42dd-b9fd-eac9f5aad457 ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=64b0b219-0478-42dd-b9fd-eac9f5aad457 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=64b0b219-0478-42dd-b9fd-eac9f5aad457 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Herman on 2008-02-04
Hello tiredtired,
Have you any idea why your first PATA (IDE) hard drive is coming up as /dev/hdc instead of /dev/hda?
I was expecting to see it as '/dev/hda'.
```
 			 				Disk /dev/hd[COLOR=Red]**c**[/COLOR]: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hd[COLOR=Red]**c**[/COLOR]1   *          63   149838254    74919096   83  Linux
/dev/hd[COLOR=Red]**c**[/COLOR]2       149838255   156296384     3229065    5  Extended
/dev/hd[COLOR=Red]**c**[/COLOR]5       149838318   156296384     3229033+  82  Linux swap / Solaris
```
I'm wondering now what drives you might have plugged in and jumpered as Primary master (/dev/hda) and primary slave (/dev/hdb)? Do you have two CD-ROM or DVD drives plugged into your primary IDE socket?

Can you recheck your hard drive cables and jumper settings for me please, and make sure they are right first before we go on setting up your software. Otherwise we might not be able to get anywhere at all. Your BIOS will be trying to boot your CD-ROM drive or whatever is plugged in an jumpered as primary master ( /dev/hda).

Regards, Herman :)

---

### Post by Herman on 2008-02-04
```
## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
root (hd**1**,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=64b0b219-0478-42dd-b9fd-eac9f5aad457 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd**1**,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=64b0b219-0478-42dd-b9fd-eac9f5aad457 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd**1**,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd**0**,0)
savedefault
makeactive
chainloader +1
```

---

### Post by tiredtired on 2008-02-04
> **Herman said:**
> Hello tiredtired,
Have you any idea why your first PATA (IDE) hard drive is coming up as /dev/hdc instead of /dev/hda?
I was expecting to see it as '/dev/hda'.
```
 			 				Disk /dev/hd[COLOR=Red]**c**[/COLOR]: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hd[COLOR=Red]**c**[/COLOR]1   *          63   149838254    74919096   83  Linux
/dev/hd[COLOR=Red]**c**[/COLOR]2       149838255   156296384     3229065    5  Extended
/dev/hd[COLOR=Red]**c**[/COLOR]5       149838318   156296384     3229033+  82  Linux swap / Solaris
```
I'm wondering now what drives you might have plugged in and jumpered as Primary master (/dev/hda) and primary slave (/dev/hdb)? Do you have two CD-ROM or DVD drives plugged into your primary IDE socket?

Can you recheck your hard drive cables and jumper settings for me please, and make sure they are right first before we go on setting up your software. Otherwise we might not be able to get anywhere at all. Your BIOS will be trying to boot your CD-ROM drive or whatever is plugged in an jumpered as primary master ( /dev/hda).

Regards, Herman :)

Hi,

The IDE drive is the secondary drive with Ubuntu installed, the SATA is my main drive with Windows. I just flashed a look at what the POST thinks, and it certainly seems odd. I'm not sure what needs to be changed, but I can tell you what it says now at least:

IDE channel 0 Master: DVD ROM drive
IDE channel 0 Slave: None
IDE channel 1 Master: The IDE drive with ubuntu
IDE channel 1 Slave: None

IDE channel 3 Master : My main hard drive with windows.

I have no idea why the DVD drive is where it is (shop put the system together for me), but I'm not sure how everything should be, either. How do the devices need to be arranged to be friendly with our dual-boot efforts? Also not sure what to do about the jumper settings. ;)

---

### Post by Herman on 2008-02-04
Presuming your SATA drive is still listed as number 1 hard drive in your BIOS, we'll install GRUB to it.
However, since Ubuntu's GRUB has your hard drives upside down, we'll be working upside down too. In other words, we're calling your SATA drive (hd1) for the purpose of installing GRUB to MBR.

This first command give you a GRUB shell
```
sudo grub
```

This second command sets Ubuntu in your first hard disk as GRUB's root device. In other words you want to install Ubuntu's GRUB somewhere.
```
root (hd0,0)
```

This third command installs GRUB to MBR in your second hard disk, well, at least GRUB thinks it's your second hard disk. Actaully, your BIOS thingks it's the first hard disk, and that's the one the BIOS is booting.
```
setup (hd1)
```
```
quit
```Now you should be able to boot properly.

Regards, Herman :)

---

### Post by tiredtired on 2008-02-04
Hi,

Did you get my post in the middle there? Just in case it changes anything. ;)

---

### Post by oygle on 2008-02-04
I wanted to do pretty much the same thing as you need, it worked out fine, see [http://ubuntuforums.org/showthread.php?t=577185](http://ubuntuforums.org/showthread.php?t=577185)

Only thing is, my primary has Ubuntu/grub on it, and it just boots into Ubuntu normally, and if I want to use the other OS, I just press ESC at grub, a menu comes up, and I select the option.

I had to modify 2 files from memory, one actually swaps the 'hd0' around if I select the menu option for the Windows OS.

HTH

---

### Post by Herman on 2008-02-04
> Hi,
The IDE drive is the secondary drive with Ubuntu installed, the SATA is my main drive with Windows. I just flashed a look at what the POST thinks, and it certainly seems odd. I'm not sure what needs to be changed, but I can tell you what it says now at least:

IDE channel 0 Master: DVD ROM drive
IDE channel 0 Slave: None
IDE channel 1 Master: The IDE drive with ubuntu
IDE channel 1 Slave: None

IDE channel 3 Master : My main hard drive with windows.

I have no idea why the DVD drive is where it is (shop put the system together for me), but I'm not sure how everything should be, either. How do the devices need to be arranged to be friendly with our dual-boot efforts? Also not sure what to do about the jumper settings. :wink: Never mind about it for now then, we'll try with the software changes anyway and if it doesn't work then you might have to get your computer shop to swap your IDE cables . Maybe it won't matter.

---

### Post by tiredtired on 2008-02-04
Sure, will just give the changes a try now.

---

### Post by tiredtired on 2008-02-04
Ok, I have installed grub to the MBR of the SATA drive.

However, I cannot edit the menu.1st file.

When I follow the commands (from earlier) to mount the drive, the drive mounts successfully. However, when I try to open it I get an empty file. And when I browse the mounted drive, the file is not there. Actually, the ubuntu directory doesn't even exitst. In other words, I can't go to

 /media/ubuntu/boot/grub/menu.lst

, as media is a dead-end. media only contains 4 folders (cdrom, cdrom0, floppy, floppy0).

However, this still *must* be the correct drive, as it has 64.8GB space free. This is about how much the IDE drive I installed Ubuntu on has free.

Anyway, earlier on I posted the contents of a menu.1st file I found somewhere else (under "File System" >>  /media/ubuntu/boot/grub/menu.lst). However, I went to edit it this time and discovered that it cannot be written to. So I can't save the changes.

What can I do? That menu.1st is unwriteable and one doesn't exist on the mounted drive.

I hope something will work, as with the MBR changed but that not changed, I am now in a position where Grub loads at boot but cannot boot either windows or ubuntu! All I have left to work with is the livecd. :(

---

### Post by oygle on 2008-02-04
It's just a permissions things, try this ...

> 
gksudo gedit /media/ubuntu/boot/grub/menu.lst


---

### Post by oygle on 2008-02-04
My primary HDD is for Ubuntu, and the secondary HDD is for windows, so your situation is very similar. Here are the files I've been using ..

device.map

```

(hd0)	/dev/sda
(hd1)   /dev/sdb

```

and the last few lines of menu.lst

```

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows
map             (hd0) (hd1)
map             (hd1) (hd0)
root            (hd1,0)
savedefault
makeactive
chainloader   +1

```

notice the 'map' commands are before the 'root' command, I don't know if that matters though ?

---

### Post by tiredtired on 2008-02-04
Hi, thanks I got the file to save!

I rebooted and got grub, and this time Ubuntu boots from it!

However, Windows will not boot. I get no error messages though. I just get to "Starting up..." and nothing happens. It seems to be hitting a snag somewhere between when it says "Starting up" and "Loading etc...".

---

### Post by Herman on 2008-02-04
We changed your Windows boot entry from this,
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```To this, 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```
I don't see what could be wrong with that now, we dropped the pair of 'map' commands because we shouldn't need them anymore.

Maybe try putting them in there again just in case they help for some reason,
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
[COLOR=Sienna][B] map        (hd0) (hd1)
map        (hd1) (hd0)[/B][/COLOR]
chainloader    +1

```

---

### Post by tiredtired on 2008-02-04
Hi,

I actually hadn't realized I'd needed to remove the map commands before. So I just removed them, and now both windows and Ubuntu boot! Success!

8-)

Thanks for all your help everybody!

---

### Post by Herman on 2008-02-04
Okay! Great work tiredtired, well done and thanks for your patience. :)
Happy Ubuntuing!
Regards, Herman :)

---

