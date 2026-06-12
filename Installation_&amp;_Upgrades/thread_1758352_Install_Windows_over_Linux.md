---
title: "Install Windows over Linux"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by dmelendez34 on 2011-05-14
I need to update my BIOS on my Acer d255 and I have tried the Linux ways to update but they are too complicated for my limited knowledge of linux. 

I was going to just use my XP disc to reinstall XP over ubuntu 10.10, then I was going to run the .exe files to update my BIOS, and then immediately put ubuntu back on and erase win xp like I did when I first bought the netbook.

Well, when I ran the disc it started the install process, loading drivers.  When it got past that point however, I never can get to the screen that ask you how you want to install windows or what you want to do with the partitions.  I get an error message that says there is a problem with my hard drive and if this is the first time i have received this error then just restart and try the install again.  Then it rambles off some other instructions if this error happens over and over again.  

The disc works just fine on my extra desktop I have at home.  I don't have any hard drive issues when I use my netbook (currently running ubuntu for the past 6 months).  I checked out the disk utility screen and it says the drive is fine.

What could be causing me to be unable to install Windows back on my netbook?  Thanks for any help guys.

---

### Post by dmelendez34 on 2011-05-14
Tried running GParted to delete partition and start from scratch but it wont boot on my netbook.  I tried the Live USB version and a boot CD but neither gets past the screen that says:

ISOLINUX 4.03 2010-10-22 ETCD Copyright (C) 1994-2010 H. Peter Anvin et al

Could I have created both incorrectly?  or is it my netbook?  I went into BIOS and told my netbook to boot from external CD-ROM drive and from USB-HDD and floppy before going to HDD.  

Even the Windows XP gets farther along in setup than GParted has.

---

### Post by dmelendez34 on 2011-05-14
I brought my netbook out to my living room so I can type out the exact error I get when I run the XP disc for install. Here it is:


A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer.  if this screen appears again, follow these steps:
Check for viruses on your computer.  Remove any newly installed hard drives or hard drive controllers.  Check your hard drive to make sure it is properly configured and terminated.  Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical Information: 

*** STOP: 0x0000007B (0xF78DA63C, 0xC00000034, 0x00000000, 0x00000000)


I am going to use a CD and USB drive version of Ubuntu to work with the partition on the hard drive...I think that may be the issue (from what I have read on the forums).

---

### Post by dmelendez34 on 2011-05-14
Tried a USB Ubuntu 11.04 drive but it didn't get past the screen that the GParted CD and USB drive got stuck on.

The CD seems to be running right now... I can see the ubuntu screen with the 5 white dots showing it is loading something.

Hopefully I can figure out how to partition the HDD for NTFS.

---

### Post by MAFoElffen on 2011-05-14
> **dmelendez34 said:**
> Tried a USB Ubuntu 11.04 drive but it didn't get past the screen that the GParted CD and USB drive got stuck on.

The CD seems to be running right now... I can see the ubuntu screen with the 5 white dots showing it is loading something.

Hopefully I can figure out how to partition the HDD for NTFS.
Sorry, saw this as I was heading out the door this morning and didn't get a chance to respond until now. I see it has now regressed into a bit of a sticky spot.

I (personally) wouldn't have installed XP just to update a BIOS,.  At the shop, we create a bootable USB thumbdrive or an usb extenternal bootable drive to update your BIOS.  Because- that's "all" you needed/wanted to do right? (Lessons learned.)  

My current view on a "Best Value" is these Pata/Sata/3.5"/2,5" USB adapter cables on ebay at $25.  They are "SO" handy.  For just taking any drive that was laying around and being able to plug it in and use it for whatever.

Now there is other problems <>  XP isn't smart enough to know not to write a boot sector over another OS'es MBR.  It has an ego and thinks it is the only OS in the world and no one else matters anyway.  (It usually overwrites the Grub Boot sector).

First, do you have a current LiveCD" Please post the results of the bootdisk script in my signature. Use the " # " button when posting and paste the results between the code tags.

Next: 
 - Have you updated your BIOS yet?
 - Do you want XP to stay?

---

### Post by dmelendez34 on 2011-05-14
I didn't want to even try to install XP to update my BIOS but I just couldn't figure out how to create a bootable USB drive with the BIOS update I needed.  

I tried installing XP this morning but I couldn't get it to get past the error message I mentioned.  

I got a Ubuntu 10.10 disc to load but I couldn't find GParted to repartition the hard drive to see if that is what was keeping me from installing XP.  

I was shutting down and rebooting a lot and now my laptop screen and/or hard drive are not working together.  Right before this happened I had entered BIOS to change the Boot order of my devices and when I saved the new settings the screen did not show anything and I could not see any HDD activity.  

I rebooted and got some HDD activity but still nothing on screen.  I have left my netbook turned off for about an hour and I am going to give it turning it on another shot.  

If I can get it back to normal I may just live with the fact that I wont be able to use my netbook without its battery (the BIOS update was to fix a glitch that would freeze the netbook when it was running on battery power).  

If you can help me get my netbook to turn back on normally I would greatly appreciate it.

---

### Post by MAFoElffen on 2011-05-14
> **dmelendez34 said:**
> If you can help me get my netbook to turn back on normally I would greatly appreciate it.Okay-- what did you do?

Will decide if you can repair and get back to squere one or have to reinstall...

---

### Post by dmelendez34 on 2011-05-14
OK my netbook is turning on again...apparently I was successful in deleting the old partitions on my hdd but that left me with nothing on my hdd.  Since my ubuntu boot cds apparently did not want to load (I have a 10.10 desktop, 10.10 netbook, and 11.04 desktop), I tried creating a bootable USB Live version of Ubuntu 11.04 using a different usb drive. 

The new one worked so it is installing right now. :)

Once this is done I would love if you could help me create a BIOS updating USB drive.  I tried creating a bootable CD using the instructions here [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)  but I couldn't get it to even burn the CD.  

I have a Windows Vista desktop I can do things on, and my netbook just finished installing 11.04.

---

