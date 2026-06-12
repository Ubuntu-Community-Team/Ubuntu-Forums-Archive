---
title: "Ubuntu Installer Ruined my entire HDD"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-09-21
I just tried to iinstall XUbuntu on my main workstation, in a dual boot configuration with Windows 2000, and a third existing NTFS partititon that contains my precious data and... as it looked like it was going to complete the installation successfully (was at the stage of downloading language packs), it suddenly notified me that "The Installer failed". :(

Well, I looked at the "Discs Manager" and it did create the Linux and the swap partitions the way I thought it would create (I chose option #2 at the partitioning stage - select the largest **free** partition). So, I rebooted the system (using the GUI, neither soft nor hard reset), expecting at least to boot to the original state but... :shock: :shock: :shock: nothing would boot for the HDD.

I used Partition Magick 8.01 to look at the drive and sure enough it seems like the entire partitioning information was lost (and probably the MBR as well). It reports: "Partition Table Error #114". There is nothing that partition magic can do here.

Now what do I do?

Is there a way to recover at least the NTFS data partition?

It seems that Partition Magic is not the tool for a horror case like that, but is there a tool that I can download to quickly solve the problem? Bummer, this really ruined my project schedule. :(

Thanks for any help or tip you can provide!
Alex

---

### Post by skymt on 2006-09-21
Sorry about your drive problems, do you have a backup? It really isn't the best idea to experiment with installing Linux (or any OS) on a machine you absolutely need to have running. Sometimes things just go wrong.

Anyway, your best option is to find some good disk recovery software. I've never needed it, so I don't have personal experience with any software of this type. However, [this program]("http://www.stellarinfo.com/partition-recovery.htm") looks like exactly what you need.

---

### Post by wpshooter on 2006-09-21
My recommendation would be that if you want to play around with Ubuntu that you get yourself an older spare machine.  IMO, anytime you try to put two different O/Ss on the same machine at the same time, you are just asking for problems, but maybe that's just me !!!

P. S. - Heck, even when putting just one O/S on a machine, sometimes you are asking for problems !!!

---

### Post by skymt on 2006-09-21
> **wpshooter said:**
> My recommendation would be that if you want to play around with Ubuntu that you get yourself an older spare machine.  IMO, anytime you try to put two different O/Ss on the same machine at the same time, you are just asking for problems, but maybe that's just me !!!

P. S. - Heck, even when putting just one O/S on a machine, sometimes you are asking for problems !!!

I dual-boot Ubuntu and XP, and it works just fine. Don't make blanket statements. You != Everybody.

---

### Post by xp_newbie on 2006-09-21
Guys, thanks for the quick replies.

Fortunately, I managed to recover the two important NTFS partitions, by simply using the old DOS FDISK (or some modified version of it that came with partition magic) to re-write the MBR. Every partitioning software that I used to look at the HDD, found those partitions, while only PowerQuest's PartitionMagic was totally stuck at the HDD. Weird.

So, I am happy now. :)
Without Xubuntu installed on that system. :(

Now... as for your advice: Would you believe me if I told you that this is the 5th Ubuntu system I have been installing lately?

Yes, 3 of them gave me very hard time (I eventually gave up on them), but I thought that I figured out all the quirks of Ubuntu so that installing it on relatively modern hardware would not cause problems (this message is written from a laptop running Ubuntu).

I was wrong. Ubuntu does not like many hardwares. :(
Why? I thought that with the introduction of Ubuntu, Linux finally reached the maturity of Windows (at least as far as hardware support is concerned).

Now of course I am going to think twice and even double that before installing Ubuntu. Whatever happened during installation should not have happened.

Regards,
Alex

---

### Post by wpshooter on 2006-09-21
> **skymt said:**
> I dual-boot Ubuntu and XP, and it works just fine. Don't make blanket statements. You != Everybody.


And just because it does work for you, does NOT mean that it is going to work for everyone.  And I think I said that you were ASKING for problems, I did not say that you would necessarily 100% have them.

Thanks.

---

### Post by nquinnathome1 on 2006-09-28
> **xp_newbie said:**
> 
Now of course I am going to think twice and even double that before installing Ubuntu. Whatever happened during installation should not have happened.

Regards,
Alex

Are you using the same disk for all your installs? Are you sure the actual data on the disk is okay? I've installed Linux (Ubuntu in many cases) on lots of machines and its always gone okay, whether it be a high end or low end system. I cannot believe that on five different machines Ubuntu has been problematic without some other problem, such as a damaged install disk. Are you using different disks/ISO images each time?

---

