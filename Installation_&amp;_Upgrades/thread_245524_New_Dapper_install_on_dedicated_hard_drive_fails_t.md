---
title: "New Dapper install on dedicated hard drive fails to load GRUB"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by dereknet on 2006-08-28
Hi I just started my 4th Ubuntu system installation, hoping finally being able to free my home desktop Windows system once and for all, but I've run into a serious problem.

I have a dedicated 40gb IDE hard drive that is in working condition AFAIK for the install.

After booting off the Dapper LTS live CD which I have used previously to install 2/4 of my other boxes and running through the installer, my system will fail to even load GRUB after rebooting. I believe there is a MBR on the drive because after changing my BIOS boot order to use my second hard drive rather than primary Windows disk the system just locks or seemingly does absolute nothing. If the drive did not contain a bootable partition it would have simply gone to the next drive on the BIOS' boot priority list, which would be my Windows drive.

After digging around on the forums I tried the installation one more time using the default format/partitioning scheme. Result: same thing.

Lastly after reading about some issue with GRUB failing to work on large partitions, I decided to partition the drive manually, 1) 200mb /boot ext2, 2) 1.5 gb swap, 3) rest ext3 ... Result: same thing.

So I'm kind of lost right now. In the system there are 3 other drives, 80gb IDE, 2x 120gb SATA (one has XP)

Any ideas? thanks!

---

### Post by confused57 on 2006-08-28
It seems when there's a combination of IDE and SATA drives, Ubuntu will install grub to the IDE drive...so you might want to set your system to bootup up first from the IDE drive.

Before you do anything, bootup with the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

If your 2 SATA drives are set up in a raid configuration, that "may" be a problem to which I'm not familiar with solving.

You might want to download the Dapper alternate cd and install with that, you can specify where you want grub installed...I'm not experienced enough to even guess where the desktop live cd may have installed grub on your system.

---

### Post by dereknet on 2006-08-28
Since I'd have to reboot to check fdisk -l, I'll tell you right off the bat that there is no hardware/software RAID system running on this machine now. I've disabled the RAID functionality in the BIOS.

When my problem was occurring the drive I dedicated to Ubuntu was set with first boot priority and I believe the installer placed GRUB on the drive that I've dedicated to Ubuntu.

I'll try downloading the alternative image tomorrow at work and see if that helps at all. Unfortunately my Internet is being disconnect tomorrow since I'm moving soon but hopefully I'll continue working on this. Thanks!

---

### Post by confused57 on 2006-08-28
> **dereknet said:**
> Since I'd have to reboot to check fdisk -l, I'll tell you right off the bat that there is no hardware/software RAID system running on this machine now. I've disabled the RAID functionality in the BIOS.

When my problem was occurring the drive I dedicated to Ubuntu was set with first boot priority and I believe the installer placed GRUB on the drive that I've dedicated to Ubuntu.

I'll try downloading the alternative image tomorrow at work and see if that helps at all. Unfortunately my Internet is being disconnect tomorrow since I'm moving soon but hopefully I'll continue working on this. Thanks!

I would have assumed that the live cd  installed grub to the IDE drive and I'm not sure installing with the alternate cd would help or not, but if you're willing to try...
Sounds like you're quite familiar with computers, so you've probably checked that the jumper settings are correct on the drive.

---

### Post by dereknet on 2006-08-28
Jumper settings are cable select and the bios correctly detects the drive as an IDE slave.

I'm seriously testing a Vista beta install :oops:  on the drive to see if the drive or if it's just ubuntu. I'm actually a 4th year engineering computer science major at UC Davis in California, so computer stuff is usually second nature... this problem is just so strange.

---

### Post by confused57 on 2006-08-28
You can use the live cd to reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

For example, if grub  stage1 is found on root (hd1,0), you might be able to 
select setup (hd1) to ensure grub is installed on the drive where Ubuntu is installed...it's just a thought to add to your arsenal.  Hopefully, someone  who has experience with your problem will read this thread.

---

### Post by dereknet on 2006-08-28
Thanks for all the info. I just pulled out my old 5.10 cd and did an install and it worked perfectly first time. Figure that :-/

So I guess I'll just upgrade breezy to dapper in the mean time. Kind of a hassle if you ask me.

---

### Post by Colly on 2006-09-25
I also can't get past "GRUB loading, please wait".
I've just installed Dapper Drake Desktop from the i386 download into a PC that has only one HDD (30GB as primary on the first IDE cable) and once CD/DVD drive (as primary on the SECOND IDE cable).  I have no slave drives.  I used the separate cables because the CD/DVD was too far from the HDD to reach with one cable.  Both drives are jumpered as Master, which shouldn't be a problem since they're on different IDE ports.  I have no SATA or any other drives.  

I tried all the fixes I read about for GRUB and the setups (using LIVECD) to both (hd0) and (hd0,0) both said "succeeded", but when rebooting from the hard drive to which Ubuntu had been installed, I STILL kept getting GRUB loading, please wait (forever?).

I used the standard installation and when given the 3 partitioning choices, I told it to erase the entire partition (option 2 of three) since I didn't have ANYTHING ELSE on the hard drive to worry about.  

Could GRUB be failing because there's only ONE OS on the drive?
After the please waiting, all I get is the blinking underbar cursor on the next line.  The PC is hung (i.e., caps lock does not change the keyboard caps status light after it hangs - that's how I test for hung PC's)
Could GRUB be failing because I have an old ATI Rage Fury AGP card in this system? I'd have thought it would come up fine in the default VGA mode even with no card specific drivers.

I'm stumped because this old PC is so simple, it shouldn't have been able to confuse something as slick as the Ubuntu install.

It's a 300Mhz Celeron (the 500Mhz Pentium III CPU had been damaged by a prior owner's sloppy cooling fan installation and the Celeron was the only spare slot-1 type CPU in my junk box.)
The PC has 256Mb of RAM

***
Oh poop! - I just tried installing KUbuntu instead and I still get exactly the same problem.

***
I've also been wondering how can I make the installation grab and use ALL of the 30GB drive.  I feel like I'm installing Windows 98 (which also would only grab the first 2GB)

***
I guess I'm going to have to try installing the "Alternate" version and learn MUCH more about how GRUB works and how to clear the MBR.  What I would LIKE to see is how to install Ubuntu to be the default and ONLY OS on the PC and avoid GRUB altogether, but I don't yet know if that's even possible. If GRUB is a multi-boot loader, I do NOT need it getting in my face.

***
(Of course I'm a noobie at this - I only first started messing with it after dinner yesterday and lost a lot of last night figuring out that the damaged PIII CPU was what was causing my "Kernel panic - attempting to abort init" failures.)

***
And now that I'm thoroughly frustrated with my aborted installs, I think I'll boot with a DOS floppy and run FDISK /MBR or maybe even my IDEFMT.EXE utility to wipe out all my mistakes before starting over.  And if Ubuntu MUST have another OS on the drive first, maybe I'll just make a little DOS 5.0 partition before starting. Whatever.  If I get the thing working, I'll update this post with what I did to fix it (and maybe what was wrong, but I'll settle for the cake without the frosting.)  ](*,)

***
UPDATE:
#1 - Apparently, it seems that the Ubuntu packages EXPECT to find another OS on the hard drive.  When I cleared the hard drive and partitions, then added a Windows partition and installed Windows before installing Ubuntu (or Kubuntu) that GRUB then worked properly in both cases. GRUB is MULTIboot loader with the emphasis on Multi, so I guess having only a single OS (Ubuntu) to choose from confuses it. 
#2 - My gripe about not using all the free space has also been resolved.  With Windows using part of the drive, the Ubuntu installation now seems to offer a new choice #2 that says "use the largest contiguous free space".  Since that happens to be ALL of the drive that is left over above the Windows partition, Ubuntu allocated all the remaining free space just like I'd wanted it to.  Whee!

side note 1: I tried Kubuntu yesterday and noticed the games I'd seen in Ubuntu LiveCD didn't seem to be present.  I like the GUI if Kubuntu, but today I'm reinstalling Ubuntu instead.  I may change my mind again. After all, this IS a test machine I'm playing with.  

side note 2: I think I found out yesterday that Wine lets you play Windows games BUT... I didn't know they had to be previously installed on a Windows partition in the PC. Duh!  There seems to be no way to install the Windows games in Ubuntu (please correct me if this is wrong.)  Hoping this new assumption is correct, I installed Win98SE in an 8gb partition of this 30gb drive and am installing Ubuntu above it, using all the remaining space on the drive.  I plan to boot with Win98 to install the W95/W98 games, then reboot with Ubuntu to play them using Wine.  Hope it works.

---

### Post by undrwater on 2007-01-10
> **Colly said:**
> I also can't get past "GRUB loading, please wait".
***
UPDATE:
#1 - Apparently, it seems that the Ubuntu packages EXPECT to find another OS on the hard drive.  When I cleared the hard drive and partitions, then added a Windows partition and installed Windows before installing Ubuntu (or Kubuntu) that GRUB then worked properly in both cases. GRUB is MULTIboot loader with the emphasis on Multi, so I guess having only a single OS (Ubuntu) to choose from confuses it. 


I'm getting the same error, but I'm going to have to disagree with Colly.  GRUB CAN boot multiple OS'es, but it is just as able to boot just ONE OS.  I am going to suppose that the scripts for grub or grub itself on the CD is broken.  I'll also have to check out the menu.lst file to see if there are other instances of OS that might be holding it up.  I'll be back! :D

---

