---
title: "Install on a PC with 2 hardware RAID disks"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by sotossko on 2007-11-13
Dear All,
I have a PC running Windows XP prof and has 2 hardware controlled RAID disks. In windows I have 3 partitions. 

I am trying to install Ubuntu 7.10 on it,  and everything seems to install alright. When I remove the CD and try to boot,  there is no GRUB running at all - it boots directly to WinXP.

I have managed to create a floppy boot disk with GRUB loader and when I boot from this disk the GRUB loader appears but I can not boot into the partition where I installed Ubuntu. I get a message that this partition does not exist!! (it is an ext3 partition and when I try Rescue I have a shell and everything seems to be there).

I have done a second try with Ubuntu Server but it did not solved anything. 

Any ideas? :confused:
S.
PS: I have read the previous messages but do not understand a bit. Could someone write some instructions for a beginner?

---

### Post by Tux.Ice on 2007-11-13
get rid of windows reinstall ubuntu

---

### Post by rkillcrazy on 2007-11-13
Tell me this....  You said you have a "hardware" RAID, right?  When you loaded Windows, did you have to hit F6 to install the RAID drivers?

11-13-07
1419 EST

---

### Post by sotossko on 2007-11-13
well, I did not istall Win XP myself - I bought the PC with them installed and it seems that the Raid works for Win. I did mention to the shop that I will install Linux as well when I made the order... (just two weeks ago)

---

### Post by rkillcrazy on 2007-11-13
> **sotossko said:**
> well, I did not istall Win XP myself - I bought the PC with them installed and it seems that the Raid works for Win. I did mention to the shop that I will install Linux as well when I made the order... (just two weeks ago)

Well, RAID is a funny thing to deal with.  I don't mean "haha" funny either :).  Windows generally needs drivers to communicate with the RAID controllers on the motherboards.  You may think you're setting up a "hardware" RAID but it's more of a "hybrid" RAID.  True hardware RAID is done on the hardware level, in the BIOS, and no drivers are needed as the hardware takes care of communications between the OS and the drives.  Then there's software RAID which is all done through the OS.  The OS directly manages the read/writes to the hard drives.  Windows cannot have a RAID system drive without a hardware or a hybrid RAID array.  You can, however, use software RAID in Windows for various secondary hard drives.  I normally build Windows 2003 servers this way...the computer has no less than 3 physical HDDs (hard disk drives) and the system drive (normally c:\) is on one of the drives.  The other 2 are set up in a mirror and that is used as a data drive.  I can reload a server but reproducing all the data is rather tough so that's the reason for having s single drive for the system drive and a mirrored set for the data.

I've been playing with RAID and Ubuntu a lot lately.  It's all pretty new to me.  However, I was able to get my system drive striped.  I've seen plenty of articles on the web about mirrors as well.  In fact, I plan on fixing my PC tonight when I get home.  I tried to set up a striped system drive and it failed.  After playing around with it in VMWare, I'm pretty sure I know where I went wrong.

Now, if you have windows on there as well, it's doubtful that you'll be able to get Ubuntu on it in its current state.  I'd be willing to bet that the RAID controller is a hybrid and you have to have drivers for Windows to use it.  If that's the case, you'll no doubt keep seeing what I saw when I was playing with my RAID setups...  Linux will not be able to use that RAID controller like Windows does since Windows uses drivers for the controller and Linux wants to use the disks.  There are other distros out there that may do it kind of like Windows but i don't know of many for sure.  Suse may but don't quote me on that.  However, the chances of Suse acting much like Windows in the ways of hardware detection and handling are rather high since Suse is headed by Novel and Novel and Microsoft are sleeping together these days :sad:

11-13-07
1502 EST

---

### Post by sotossko on 2007-11-14
Many thanks for sharing your experience. I have tried Fedora 7 just a while ago and it seemed to recognize the RAID, installed GRUB in MRB (I know that was not so smart...) but could not start FC7 when I rebooted (no problem with WinXP so far!).

Suse is too slow and I wanted to avoid it, but at the end I will give it a go if I can not do anything else.

The sure thing is that I will have to abandon Ubuntu (something that I am reluctant to do since I can have all the packages that I want with a click)
Anyway, many thanks
S.

---

### Post by rkillcrazy on 2007-11-14
> **sotossko said:**
> Many thanks for sharing your experience. I have tried Fedora 7 just a while ago and it seemed to recognize the RAID, installed GRUB in MRB (I know that was not so smart...) but could not start FC7 when I rebooted (no problem with WinXP so far!).

Suse is too slow and I wanted to avoid it, but at the end I will give it a go if I can not do anything else.

The sure thing is that I will have to abandon Ubuntu (something that I am reluctant to do since I can have all the packages that I want with a click)
Anyway, many thanks
S.

I understand your issues.  I too disliked Suse but it was more 'cause of my prejudice against Microsoft and since Novel & Microsoft are buddies these days, I just didn't want to use them.  However, Suse played nice with Microsoft networks & Active Directory so it does have its place.  However, for now, its place is **NOT** on my hard drive.

Ubuntu is well supported and has even gotten a foot-hold in some of the larger markets.  You know you're doing something right when Dell (I hate them too) starts offering your OS as an alternative to Windows Vista!  Now, I hear Walmart is even selling PCs with Ubuntu as well.  So between Dell and Walmart, Ubuntu is gaining some ground in the consumer-PC world.

Nonetheless, you'll never hear me belittle another Linux distro.  Feel free to plug and pray with the others.  You may find one to your liking and you may stick with it.  However, you may come back to Ubuntu after you've gotten more comfortable with Linux in general after using some of the "more user friendly" OSs.  Ubuntu is plenty friendly but others are more warm and fuzzy and that tends to help warm people up to an new OS.

11-14-07
0905

---

