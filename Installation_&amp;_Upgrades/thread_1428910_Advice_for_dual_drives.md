---
title: "Advice for dual drives?"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by orenpaulhanner on 2010-03-13
Hi everyone !. I am finally installing KK after much playing around. What I would like to get is some advice. I have a HP Laptop with dual d rives. I know I am a newbie on here, but yes, I had two drives installed. Both are 250 Gig Sata drives. Vista of course is installed. I would like to dual boot with 9.1. My biggest question is, how big to make the partition? I do plan on downloading some games and programs for 9.1. I was going to go with the 30 Gig install on the second hard drive. If I ever exceeded that partition size, does it act like Windows and automatically increase in size as you add more programs? Thr reason I was looking at the second drive was because there is a recovery partition on the first drive, along with Vista's install.  Although there would be enough partitions available to use (for swap and one for install) perhaps that may be the way to go. I do have quite a bit of music and movies as well. KK will see an NTFS partition and would be able to read files form it, so I'm ok with that. In short, I don't wanna short sell a partition. I do have the space to do what I need to do. Also, I have an older laptop with dual 100 Gig drives thjat I would pretty much do the same too as well.
    After typing all of this, it seems to make sense. Should I keep both operating systems on one drive and use the second as a NTFS drive for storage? Also, how big should I make the partitions? Any advice would be greatly appreciated ! ! !  ! !

---

### Post by raymondh on 2010-03-13
> **orenpaulhanner said:**
>  Should I keep both operating systems on one drive and use the second as a NTFS drive for storage? Also, how big should I make the partitions? Any advice would be greatly appreciated ! ! !  ! !

That would be nice.  But, consider for a moment, should your OS drive fail ........ ?

My preference in a 2 HD set-up is to keep windows in 1 HD while the other OS in the 2nd HD.  As for data storage, you can choose any HD to create the partition (NTFS) which could be mounted, accessed and or shared by either OS.  Just remember to keep regular back-ups.  A good recovery system is to also make regular images of your system.

How would I go about this?

1.  Set the Ubuntu HD as first to boot in BIOS.
2.  Install Ubuntu to that HD.  Also, install GRUB to the MBR of that HD (which, by reference to no.1 above, is already first to boot in BIOS).  That way, should Ubuntu 'faint' on you, you have your windows and its' MBR intact.
3.  Shut down, do a quick bios change to boot the win HD first, boot up and check that windows is booting normal and ok.  If booting into grub, you had just installed GRUB in the win HD and we'll need to fix that.
3.  If ok, shut down, change the BIOS order again to make the ubuntu HD first to boot, boot up into ubuntu and update ... If you  noticed that GRUB did not present you with a windows option at start-up, you'll need to update GRUB as well. Reboot again.

That would be my 2-cent advice ;)  

Either way you proceed, have a working/tested back-up of your files.

Best,

Raymond

---

### Post by oldfred on 2010-03-13
I agree with raymondh. Each drive should have its own operating system. The rest can be for data. I only had root and swap for 3 years with a small partition for shared data with windows. If you are keeping your data in shared partition(s) you do not need much space. Root can be 10-20GB, but I would still make a separate /home for your linux data and (hidden) settings. It makes it easier to reinstall in the future. Linux programs are not large so you do not need huge amounts of space for root. 

I also do not believe windows automatically expands partitions.

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by orenpaulhanner on 2010-03-13
So, if I have this correct....

Install Ubuntu on the second drive. Say with, 30 Gig os space. Keep the rest as ext4. (Besides the 2 Gig for swap)

Restart, change BIOS to select second drive as first boot device.

Let Ubuntu start up, get all the changes and updates made.

Restart, change BIOS again, back to Win drive. set as first boot device.

The only part I wouldn't be sure of is setting GRUB up?

---

### Post by oldfred on 2010-03-13
Grub will auto install to the drive set as first in BIOS. It is easier to change drives in BIOS before installing or else grub will overwrite the windows installer and you will have to reinstall both grub and the windows boot loader. Reinstall of boot loader is not difficult from a liveCD after you have done it several times which we all learn to do eventually.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

There also is a good way to install a generic windows boot loader directly from linux. The windows boot loader only looks for a partition with a boot flag and continues to boot from that partition.

---

### Post by Mark Phelps on 2010-03-14
Just to add my 2-cents --- heartily agree with Raymondh and Oldfred.  

I have a multi-OS machine and use separate drives for MS Windows installs from Ubuntu installs. This prevents the MBR-overwrite problem and makes it easier to repair OSs without worrying about collateral damage to the other installs.

---

### Post by raymondh on 2010-03-14
+ 1 on OldFred.

Set BIOS first.

Regards,

Raymond

---

### Post by orenpaulhanner on 2010-03-16
Ok. So the grub will let me keep sanity if I wipe my Vista drive, or something happens to it then, I am guessing. Will I need to create a home folder in Ubuntu as well? I know I have been dragging this out a bit, but I am a bit OCD'ish when it concerns my computers, lol. I may be putting this on a couple of more machines. I have played around with Ubuntu a few times and everytime I do, it gets harder to go back to windows.....

---

### Post by raymondh on 2010-03-16
The advice to set BIOS first is 2-fold:

1.  If you do a default ubuntu install, GRUB will default install in the HD that is set to boot first in BIOS .... and,
2.  You are (therefore) retaining the windows HD as original as possible.  That also means that you retain the windows bootloader .... which some people like .... just in case you decide to go back to the original windows configuration.

Now, GRUB has the ability to read and access the operating systems (ubuntu and windows).  That is why it was suggested earlier to use GRUB.  If needed, usually a GRUB update is all that is required to 'update' it's (grub's) configuration files.  There are a lot of tutorials in the forum on how to update GRUB2.

For your other question regarding a /home partition .... I personally prefer to have my /home (where my settings, files, etc) reside separate from root (/), which is where the ubuntu system files reside.  That way, should I need to reinstall ubuntu later on for any reason, I just reinstall OVER the existing root partition .... hence keeping my /home (and my settings, etc) intact.

In partitioning, we all have a 4-limit.  That is ... we can ONLY create either:

- 4 primary partitions ; or,
- 3 primary partition AND 1 Extended partition.  Of course, the EXTENDED partition can have as much logical partitions in it.

That said, depending on what is in your soon-to-be ubuntu HD, you will have to decide on how/what partitions to create.

 I am glad you are OCD-ish (your words :)  ).  Keep the questions coming.  Here is a dated, but very relevant reading material from bodhi.zazen

[http://ubuntuforums.org/showpost.php?p=1646977&postcount=1](http://ubuntuforums.org/showpost.php?p=1646977&postcount=1)

Have fun ... read and ask a lot.  Happy ubuntu-ing.

EDIT ... If you wipe your Vista drive, then you lose your Vista.  That is why in partitioning, you have to identify the proper/appropriate drive.  Some folks, to be sure, have gone as far as detaching the drive they don't want affected.  You can do that but later on will be required to mount (and update grub2) the detached drive or ... be careful when installing.  

If anything happens to it, then you'll have the challenge of trying to access it's (Vista) files.  Always have a working/tested back-up of your files.

Raymond

---

### Post by orenpaulhanner on 2010-03-18
Thanks for the tip ! Like I have said, I am getting more and more comfortable with Ubuntu and love it more. So, a couple of ideas and a couple of questions, then I should be set.

On my second hard drive, I will partition it as NTFS, and use 20 Gigs to install Ubuntu with 1 Gig for swap, and possibly 5 Gigs for either home or data. My question concerning that is: If I allow 20 Gigs for Ubuntu, does that mean that will limit any programs, etc to using that 20 Gigs only? I ask because on an NTFS drive and Vista, the hard drive (in-use) will increase as you install more programs. Does Ubuntu do that as well? I hope that makes some kind of sense.

The first drive that will have Vista will have the grub thrown on it as well. I think I can manage that. Install Vista on the first drive, format the second with NTFS, make it bootable as the first device, install Ubuntu, updates, etc. Install GRUB on the first drive after setting it to become the first device again. Jeez, I thought it woulda been easier to just follow the guide for a dual boot system using two different hard drives. Whatever works and seems to be the best, plus, I get all kinds of advice on here !

---

### Post by oldfred on 2010-03-18
You do not need grub on the Vista drive as you will be booting from the Ubuntu drive.
Install Vista to drive 1
Vista/windows boot loader in the MBR & Vista install, possible partitions for data

Set BIOS to boot 2nd drive
Install Ubuntu, grub goes into MBR and root can be 20GB swap 2 GB or more, rest /home or /data.

I have installed lots of applications and my root has expanded all the way to 5.5 GB. Most of my data is in shared partitions with windows as NTFS or data partitions as EXT3.

---

### Post by raymondh on 2010-03-18
> **oldfred said:**
> You do not need grub on the Vista drive as you will be booting from the Ubuntu drive.
Install Vista to drive 1
Vista/windows boot loader in the MBR & Vista install, possible partitions for data

Set BIOS to boot 2nd drive
Install Ubuntu, grub goes into MBR and root can be 20GB swap 2 GB or more, rest /home or /data.

I have installed lots of applications and my root has expanded all the way to 5.5 GB. Most of my data is in shared partitions with windows as NTFS or data partitions as EXT3.

+1 on OldFred

:)

Raymond

---

