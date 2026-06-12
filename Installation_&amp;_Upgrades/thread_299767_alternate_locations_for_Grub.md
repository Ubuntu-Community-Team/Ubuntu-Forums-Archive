---
title: "alternate locations for Grub"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by bullinchinashop on 2006-11-14
I'm downloading the alternate cd for 6.10 right now.

I just discovered that in addition to the usual suspects my computer's BIOS will also allow me to boot from a usb floppy or usb zip. There is also a "boot from other device" option.
So...
Is there any way I can make Ubuntu write Grub to a zip disc or a usb thumb drive instead of a floppy?
I'm not completely opposed to getting a floppy drive but a 750 MB zip drive is way more useful than a floppy and a thumb drive is a lot more durable and definitely cooler than a zip disc.

---

### Post by Herman on 2006-11-15
I hope they fixed the Alternate CD for Edgy since the one I tested, which passed the md5sum test, but didn't pass it's own 'check CD for defects test, and couldn't complete an install.
I used the Edgy 'Alternate R.C.' CD, and had a lot of updates instead, (80 or so).
The Dapper Drake 'Alternate' Install CD works well.

You should be able to specify anywhere to install a bootloader if you use the 'Alternate' CD, see my sig link for details.
I haven't tried installing Grub to a USB device, but it's a good idea. I'll try that soon. I think it would be best to have the device plugged in from the beginning of the install, so it will be detected by the installer. I am not sure how to specify the USB thumb drive as the device to install Grub to for the installer. I will need to play with that a few times before I'd be ready to give anyone advice on the subject..

Regards, Herman :D

---

### Post by bullinchinashop on 2006-11-15
Once you find out what name it assigns to the thumb drive it should be as easy as telling it to install Grub there. I think I'm gonna have to try this. I'll post my results if I do and explain how I did it.

---

### Post by Herman on 2006-11-16
Thanks bullinchinashop ,
The md5sum for the Edgy i386 'Alternate' CD.iso I  had problems with is 549ef19097b10ac9237c08f6dc6084c6. That one red-screens during one of the final stages of installation in my computer.
Does it do the same for you? If it does do the same to you, I'll find out more details and possibly file a bug report on it.  It might  only be my computer, I don't see too many others complaining, unless I'm the only one in the world still left using the 'Alternate' Installer. 

The Edgy Eft ubuntu-6.10-rc-alternate-i386.iso 2a5316d26a164db5ca633b68a5ca9faf works well for me.

I'll try another test install and see if I can install Grub to a USB thumb drive too and we can compare notes. I think that part will be easy for me, as I have a computer with two IDE disks, and I think the thumb drive will come up as an scsi disk, so I'll try typing 'dev/sda' for a location to install Grub to, and see if that works. 

Regards, Herman :D

---

### Post by Herman on 2006-11-16
I did it! :D

My first attempt was only a partial success, I tried using the Edgy Eft 'Alternate' RC CD 2a5316d26a164db5ca633b68a5ca9faf and used the first method described in this link to install Grub to the USB thumb drive. 
[HOWTO: Restore GRUB (if your MBR is messed up)]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub") [2]("http://www.ubuntuforums.org/showthread.php?t=24113&page=2&highlight=grub") [3]("http://www.ubuntuforums.org/showthread.php?t=24113&page=3&highlight=grub") ... [Last Page]("http://www.ubuntuforums.org/showthread.php?t=24113&page=9&highlight=grub"))                                                                                         vnbuddy2002
The result of that was Grub was installed to MBR in the Thumb drive alright, but it kept bringing up my boot menu from an installation I have on my second hard disk. I tried adding a /grub directory so it would have a menu.lst and all the other grub files to itself and configuring the menu.lst, but that had no effect.
At least this experiment confirmed that my USB thumb drive does come up as a partitionable disk in the installer, and /dev/sda is the correct location to have Grub installed to, at least for my particular machine.

My second attempt has been successful.
I installed Edgy to my first IDE hard disk, with /dev/hda6 as '/' (the root of the filesystem. I formatted the thumb drive and mounted it as /boot,  to install the kernel and initrd and /grub there and other files. When I got to the step where we choose to install grub to MBR, (yes, no or go back), I chose 'No', and once again typed /dev/sda on the line in the subsequent box for where to have Grub installed instead.
When my system rebooted, I saw my new Grub menu, but it wouldn't boot the new installation or any of my pre-existing Ubuntu installations, (I have four of them in this machine). I got all kinds of error messages. It did boot Windows, and I have [WinGrub]("http://grub4dos.sourceforge.net/") in Windows at the moment, I could have used that to boot my other systems, but that wasn't the challenge at the time.
Instead, I used the Thumb drive's Grub [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")  to conduct a few simple tests to find out how the USB drive's Grub sees my hard disks. I found out that the USB drive itself is seen by its' Grub as (hd0), making my first hard disk, which is usually (hd0), seen as (hd1) as far as the thumb drive's Grub is concerned. My second hard disk has become (hd2), according to my USB drive's Grub. Funny thing that Windows boots okay as (hd0,0).
Clearly then, I needed to edit my thumb drive's menu.lst with the appropriate changes to the hard drive numbering. To do that. I booted up one of my other Ubuntu installations by a[ CLI Direct Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."), and opened my Thumb drive's  menu.lst from there, (sudo gedit /media/usbdisk/grub/menu.lst). The edited file works perfectly, I rebooted successfully into my newly installed 'Edgy Eft' system, with /boot in my USB drive and /root in my first hard disk. :D

I don't think this idea would be very easy for the average new user to attempt. A Linux user with a little Grub experience should be able to follow what I have done alright. 

Regards, Herman :D

---

### Post by confused57 on 2006-11-16
> **Herman said:**
> Thanks bullinchinashop ,
The md5sum for the Edgy i386 'Alternate' CD.iso I  had problems with is 549ef19097b10ac9237c08f6dc6084c6. That one red-screens during one of the final stages of installation in my computer.
Does it do the same for you? If it does do the same to you, I'll find out more details and possibly file a bug report on it.  It might  only be my computer, I don't see too many others complaining, unless I'm the only one in the world still left using the 'Alternate' Installer. 

The Edgy Eft ubuntu-6.10-rc-alternate-i386.iso 2a5316d26a164db5ca633b68a5ca9faf works well for me.



Regards, Herman :D

Herman,  I plan on installing Edgy, using the i386 alternate cd(same md5 sum as you listed), on a new SATA that I'm getting soon...I've never had a SATA drive, but if things go well I'll let you know how the install goes.  I've installed Edgy using the Knot2 alternate cd successfully, I wasn't aware of problems with the final alternate iso...the alternate cd  just allows more control of the installation for me.

---

### Post by Herman on 2006-11-16
Thanks confused57,
I burned the same .iso file to a brand new CD-RW and this time it passed it's 'check CD for defects' test and had satisactorily completed an install.
I guess I spoke too soon. I was sure I tried everything too. I wonder what was wrong. Anyway, I'm happy now :D Sorry for any inconvenience to anyone.
Edgy Eft 'Alternate' CD 549ef19097b10ac9237c08f6dc6084c6 seems to be okay now.

How did it work for you, confused57?

Regards, Herman :D

---

### Post by confused57 on 2006-11-18
> **Herman said:**
> Thanks confused57,
I burned the same .iso file to a brand new CD-RW and this time it passed it's 'check CD for defects' test and had satisactorily completed an install.
I guess I spoke too soon. I was sure I tried everything too. I wonder what was wrong. Anyway, I'm happy now :D Sorry for any inconvenience to anyone.
Edgy Eft 'Alternate' CD 549ef19097b10ac9237c08f6dc6084c6 seems to be okay now.

How did it work for you, confused57?

Regards, Herman :D
Herman,
Sorry for the delay, finally received and installed my new SATA drive...bios and my Dapper install recognized it immediately.  The Edgy alternate cd seems to have installed with no problems...I haven't completely configured everything, but the install is working great so far.
I had burned the alternate iso to a CD-R, so it may have been your media initally, as you've already ascertained.
Thanks for all your help(your advice & website have been invaluable for me more than once),
                          JB

---

### Post by Herman on 2006-11-18
Thanks for confirming that , confused57, I feel silly for thinking there was something wrong with the .iso now, in hindsight. I wouldn't have said so if I hadn't tried pretty hard first, and it's not as if it's my first time either. It's not often that I complain about anything either. I guess it just goes to show the value of these md5sums and 'check CD for defects' tests. They really do help if people use them.
Anyway, I'm glad it was a false alarm, my new 'Alternate Cd works fine too. :D

---

