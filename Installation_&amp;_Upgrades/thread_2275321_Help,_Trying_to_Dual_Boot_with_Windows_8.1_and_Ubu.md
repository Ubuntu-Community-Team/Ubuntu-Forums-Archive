---
title: "Help, Trying to Dual Boot with Windows 8.1 and Ubuntu 15.04 with UEFI"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Sithtiger on 2015-04-25
Hi, I've had Win 8.1 installed for a while and hadn't had Ubuntu installed in a while. Since then I've upgraded my system and now I've got a mobo with UEFI instead of BIOS. I want to install Ubuntu 15.04 but I've ran across so many different articles saying how this and this might work and there are so many different suggestions. I don't know why to do. I just want to something that works. I'm going to put Windows 10 on this system when it comes ou the end of July or so they say and then I want install Win 10. I imagine I'll have to do a full format to do this and basically start all over again...sigh. 

I've heard so many things to disable in the BIOS/UEFI and/or don't touch, I just don't know what to do. Then I'll have to install 15.04 or whatever their latest update is at that time and battle it out with the UEFI again. I'm a relative beginner to the Linux stuff and I just need a little help installing help with the install and would REALLY appreciate any assistance anyone would give.

Quickly, my system specs are CPU: intel i5-3570K@3.40, RAM DDR 3 16 GB, MSI Nvidia GTX 970 2x SLi), Crucial MX100 256 GB SSD, Seagate, WD 2TB Hybrid HD, LG Bluray burner and MSI Z77 Mobo and finally Windows 8.1 x64 Pro.

Everything seems to be running perfectly. I have about 233 GB free to play with on my hybrid drive. I seem to recall running across some program that would setup some sort of boot that would make these UEFI effectively moot, but I can't seem to recall the name of said program. At any rate, any help would be much appreciated. Thanks in advance.

 TL;DR: I have Win 8.1 already installed and I have an UEFI (BIOS) installed, which seems to give great difficulty installing because of that.  Thanks in advance!!!

---

### Post by oldfred on 2015-04-25
Does the Ubuntu live installer work in live mode?

My UEFI desktop with an Asus motherboard works with both 14.04 & 15.04, but no Windows. I just installed to a Dell SFF system with Windows & all the Windows backups took a couple of days as other things and going to store for more  flash drives added time. I made Dell recovery, Windows recovery, and full backup onto 5 DVD, & 2 flash drives. 
But then with Windows shrink to 50GB on 1TB drive, fast startup off in Windows and pre-partitioned, I was able to install 15.04 in 10 minutes in UEFI mode. And it just worked. But that is also with Intel video.
You may have some issues with nVidia 970 cards.
       The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

Besides Windows fast startup may be a UEFI setting for fast boot. Best to have that off. My Asus had a setting where I could set it to a 3 sec delay.

 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

---

