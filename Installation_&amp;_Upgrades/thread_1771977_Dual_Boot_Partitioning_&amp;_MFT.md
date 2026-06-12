---
title: "Dual Boot Partitioning &amp; MFT"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by tomwbro on 2011-05-30
Hello. I am getting ready to install Ubuntu on my brand new HP desktop running Windows 7 64-bit. I want a dual boot setup because I will need Windows for work-related projects, but use Linux for everything else.
 
When I tried to shrink the main Windows partition of 1 TB, Windows said the maximum I could shrink it was 500 GB. After a defrag, I learned this was because there are system files excluded from the defrag process stored in the middle of the drive, including the MFT (or backup space reserved for the MFT). I defragmented with Windows, PerfectDisk, and MyDefrag, all with the same result.
 
I have not found a reliable source indicating that the MFT and excluded files can be moved up closer to the beginning of the partition. 
 
Then I read that when you use the disk partitioning tool included in the Ubuntu installation process that it will effectively move the troublesome excluded files when I set the partition space. Is this true?
 
I tried it, but didn't have the guts to click "install". I started the Ubuntu installer and it says Windows takes up about 32 GB. I moved the slider back and forth that chooses the amount of space reserved for Windows and the amount reserved for Ubuntu. But my concern is that if I do it this way, the MFT and other system files will be lost and Windows will have trouble on reboot.
 
My goal is to leave 50 GB (or even 100 GB) for Windows and the rest for Ubuntu. 500 GB for each OS won't cut it.
 
Thank you in advance for you help.

---

### Post by Mark Phelps on 2011-05-31
Yeah, I know it's frustrating when the Disk Management utility doesn't allow you to shrink as much as you want -- but if you bypass that and force it, you run the risk of corrupting your Win7 filesystem, leaving it unbootable and unusable.

My suggestion is to LEAVE IT ALONE.

OH, and before you do anything else, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  That will provide you the means to restore your Win7 boot loader, should it become corrupted during your dual-boot install.

---

### Post by psusi on 2011-05-31
You won't loose anything resizing.  Either it will move the MFT, or it will tell you it can't do it.  I'm pretty sure it will move it.

---

### Post by Quackers on 2011-05-31
It may also be worth checking how many primary partitions are currently in use.
HP have a nasty habit of using all 4 for one purpose or another. If you already have 4 primary partitions don't create any more until one has been deleted. The ramifications are severe, if you make that mistake!

---

### Post by tomwbro on 2011-05-31
Thanks, Mark. Yes, I have my Win7 repair CD. That was the first thing I did.
 
Psusi - If you think it will move the MFT, do you think it will also tell Windows where it got moved to?  That's my other concern.
 
The HP model p6724 came with three partitions: 100 MB SYSYTEM, 13 GB HP_RECOVERY, and 918 GB OS.
 
I'm still researching and have not tried the installation yet.  Does Microsoft make available a copy of Win7 since I purchased a PC running it?  It's been awhile since I bought a new computer... the last one I bought came with a back up copy of the OS on CDs.  In other words, if the Ubuntu installation screws everything up, is it possible to wipe the disk and reinstall Win7 so it's just like new?
 
Thanks for your input.
 
Tom

---

### Post by psusi on 2011-05-31
> **tomwbro said:**
> 
Psusi - If you think it will move the MFT, do you think it will also tell Windows where it got moved to?  That's my other concern.

Of course; that is kind of what it means to move it.

---

### Post by Quackers on 2011-05-31
There may be a utility on the system to make a set of recovery dvd's.

---

### Post by tomwbro on 2011-05-31
Thanks.  It looks like I can make Win7 recovery DVDs.  I will do that as soon as I can buy some, and will hold off the installation for now.

---

### Post by tomwbro on 2011-06-02
Ok, so I made my recovery DVDs and went ahead with the Ubuntu installation.  Everything went fine.  There's a little configuration to be done, but the dual boot set up works perfectly.  Thanks for the help.

---

### Post by holcepl on 2011-06-03
I know I am a little new to the forums... however I'm looking around the installation section and found your problem interesting. I am planning on taking the plunge and working a dual boot system. 

Anyway, have you looked at this yet? [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

It mentions a program called PerfectDisk and I believe it addresses the MFT issue you may have.

---

