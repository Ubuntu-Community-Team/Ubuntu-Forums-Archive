---
title: "Windows Vista and Ubuntu"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by jechadwell99 on 2013-08-20
I try to install Ubuntu along with Vista but the Ubuntu installer does not give the option to install alongside Vista. I do not want to delete Vista as my parents would get annoyed. How do I get Vista to boot alongside Ubuntu?

---

### Post by Mark Phelps on 2013-08-20
What you're attempting to do comes with serious risk, because if you hose up the boot loader (a possible outcome of dual booting), Vista will not boot, and you will have no way to repair it.  With Win7, there is a feature to create and burn a Win7 Repair CD -- which can then be used to repair the boot loader, but (from what I recall years ago), Vista has no such feature.

Furthermore, if you use the Ubuntu installer to shrink down Vista (as SOME here will tell you to do), that pretty much guarantees that the Vista filesystem well get corrupted, leading to the first problem mentioned above.

Seriously, you should leave your parent's machine as it is -- if you hose it up, what are they going to do then?

An alternative, if you're only interested in experimenting with Ubuntu, is to install it to an external drive.  That will prevent risk of damage to Vista.  To do that, you would need to disconnect the internal hard drive during the Ubuntu installation to ensure that the Vista boot loader does not get compromised.

---

### Post by jechadwell99 on 2013-08-20
What about installing on windows xp? We have an old desktop computer that I might be able to install Ubuntu on.

---

### Post by jechadwell99 on 2013-08-21
Why haven't I read that Ubuntu and Windows don't work together? A lot of people on the internet have had success by following the internet tutorials.

---

### Post by coffeecat on 2013-08-21
Ubuntu and Windows do work well together - I've been installing Ubuntu to create Ubuntu/Windows dual-boots for years now. Mark Phelps was simply giving you good advice, telling you the sort of things that could go wrong, and a couple of things you need to think about with Vista in particular. The sort of things we see time and time again on these forums when people have made mistakes during installation or ploughed on without adequately researching what they need to think about. And you need to be doubly cautious if you were contemplating installing Ubuntu on your parents' machine, particularly if they might get annoyed! :wink:

The damage to Vista that Mark Phelps mentioned which can occur if you shrink the Vista partition with the Ubuntu installer is a quirk of the way Windows stores bootloader files in the C: partition, and can affect Windows 7 too. It is usually repairable **if** you have access to a Vista installation disc, which you probably don't.

If this is your first attempt at installing Ubuntu, then installing on an older machine with XP is a good idea. You'll gain invaluable experience that way. Post some specifications of the XP machine and people will be able to help you. Include things such as CPU, RAM, graphics, hard drive space, because Ubuntu with Unity might be a bit heavy for some older machines and people will be able to suggest alternatives in the Ubuntu family.

---

### Post by jechadwell99 on 2013-08-21
So what you're saying is that if I do it carefully then it will work?

Also isn't it possible to create a repair disk for Vista?

---

### Post by coffeecat on 2013-08-21
> **jechadwell99 said:**
> Also isn't it possible to create a repair disk for Vista?

In theory, yes, but it requires some hacking in system files, unlike with Windows 7. And since this is your parent's machine I'm not going to tell you any more. A repair disc with the repair console is a very different thing from an OEM recovery disc in case you are confusing the two.

You've mentioned an XP machine. Why not start with that? It's a good way to begin your Ubuntu adventure and I wish you will with that.

---

### Post by jechadwell99 on 2013-08-21
Sorry about saying I could install it on the Windows XP machine. Apparently I'm not allowed to use it...
Do you know somewhere where I can get reliable information about installing Ubuntu alongside Vista?

---

### Post by Mark Phelps on 2013-08-21
You can PURCHASE the ISO file needed to burn a Window Repair CD from the following link: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

A Win7 disk will work just as well (in fact, some claim better) as a Vista repair disk. 

It's been so long since I used Vista that I don't recall, but you need to look in the Backup options to see if there is one to create a Startup (or Repair) disk.  I don't think they had one.  I think they introduced that with Win7.

I never said that Ubuntu and Windows don't work well together -- but that is not the issue here.  You're not talking about intercommunicating between two running OSs; instead, you're talking about installing a second OS on someone else's PC.

And, if that fails (as it might), you end up trashing THEIR PC, not yours.

If you are determine to charge ahead with dual-booting, then read the info below BEFORE you do that:

If you're going to dual-boot, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Vista Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

Use only the Vista Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Vista, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.

Once you have Vista shrunk, when you then boot back into the Ubuntu installer, use "something else" to do the partitioning.

---

### Post by jechadwell99 on 2013-08-22
It says I have a C: drive and an HP_RECOVERY (D:) drive. Is that OK? 
I do not know how to find out what type my drives are. How do I find out?
Also before installing Ubuntu will I need to defragment my drive?

Thanks for your help!!!

---

### Post by Mark Phelps on 2013-08-22
You need to look CLOSELY in the Disk Management screen to see ALL the partitions on your disk.  If this PC came preinstalled with Win7, there is undoubtedly another partition as well -- a small, boot partition, at the beginning of the disk.  That would make three partitions.

If there is also another one, that would make four -- preventing you from creating any more partitions for Ubuntu.  If you have four and you force the creation of another, it will automatically convert ALL the partitions into Dynamic Disks -- something you do NOT want to do.

Also, you need to create the Repair CD as I mentioned in an earlier post, BEFORE you charge ahead.

Defragmenting the "C" partition (it's not actually a "drive") would allow you to shrink it more than it otherwise would permit.

You absolutely need a way to recover from any dual-boot problems if you're going to do this.  So, you need an external drive to hold a backup of Vista -- so you can restore it if anything goes wrong.  If you don't have that, or can't get an external drive, I STRONGLY recommend that you do NOT proceed with the dual-boot setup as any problems could then render the PC unusable.

---

### Post by oldfred on 2013-08-22
If your Vista has the service pack (which it should) then it was upgraded to let you make the repair disk or CD.

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

    
From Ubuntu live installer may be best to post partition table.

sudo fdisk -lu

---

### Post by jechadwell99 on 2013-08-23
So if I follow the instructions at this link ([http://www.intowindows.com/how-to-create-a-system-repair-disc-in-windows-7/](http://www.intowindows.com/how-to-create-a-system-repair-disc-in-windows-7/)) then will I get a repair disk? I use Norton to back up my system files every month or so. And please.... How do I see if my disks are Dynamic Disks?

---

### Post by jechadwell99 on 2013-08-23
Hello..... Can I prepare a repair disk from this link? [http://www.intowindows.com/how-to-cr...-in-windows-7/]("http://www.intowindows.com/how-to-create-a-system-repair-disc-in-windows-7/")

---

### Post by Mark Phelps on 2013-08-23
That link is for Windows 7, not Vista, but as oldfred mentioned, if you have the SP installed in Vista, you should see those options.  If you walk through that process and see the repair disk options, then you can create a repair CD.  But understand -- this only provides the ability to repair boot problems, it is not a Vista restore CD.

What kind of backups did you take with Norton?  I remember Norton GHOST provided the ability to image off your "drive" to external media and to also restore from external media.  IF you took those kinds of backups, you're OK.  If you just backed off some files, that won't work to recover the OS.

As to Dynamic Disks, if you look in the Disk Management utility, it will list out all of your physical drives and the partitions on them.  It will say whether they are "basic volumes" or "dynamic disks".

---

### Post by jechadwell99 on 2013-08-23
I use Norton 360 to do the backup. 
And as for the disks... Disk Management lists the two disks I mentioned before and it says that their types are both Basic. 

About getting a system repair disk. My system came with Vista on, although it seems to have some sort of recovery partition (could that be used instead?), the computer is very old, and I live in Nepal (Just above India if you didn't know). I cannot really get a disk from the UK.

---

### Post by BazBear on 2013-08-23
If you insist on doing a "dual boot" on your parent's Vista system, use the 12.04 LTS Windows installer. By all accounts this causes a performance problem on the *buntu install, but I'm using this on my roomy's desktop Vista system and it seems to work quite well. You will be limited to a 30 GB "partition" though (that said, Ubuntu can read and write from the NTFS part of the HDD so the storage space issues aren't as bad as they may seem at first glance). You also *can *upgrade to newer versions of Ubuntu from a Windows installer install... I've done it successfully right up to the latest 13.04, but others have had issues with such upgrades. 

The beauty of the Windows installer version is, that is it's hosed or you don't like it etc., can be simply deleted from the Windows add/remove programs application found in the control panel.

---

### Post by jechadwell99 on 2013-08-23
I do not want to use the windows installer as that means that ubuntu is entirely dependant on windows.

---

### Post by jechadwell99 on 2013-08-24
Is windows vista service pack free? I'm trying to make a repair disk at the moment.

---

### Post by jechadwell99 on 2013-08-25
Somehow, even though I am using SP2, I cannot find the repair disk tool. Would this link help me make a vista repair disk? [http://www.techrepublic.com/blog/windows-and-office/creating-a-windows-vista-recovery-cd/](http://www.techrepublic.com/blog/windows-and-office/creating-a-windows-vista-recovery-cd/)

---

### Post by oldfred on 2013-08-25
The Neosmart site used to be a free download. Something about copyrights and now they charge.

---

