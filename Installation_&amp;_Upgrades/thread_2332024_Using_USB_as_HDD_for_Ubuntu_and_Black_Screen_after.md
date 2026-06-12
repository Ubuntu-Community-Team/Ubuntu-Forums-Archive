---
title: "Using USB as HDD for Ubuntu and Black Screen after choosing &quot;try without installing&quot;"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by colemilne54 on 2016-07-27
So my goal of this installation is to keep windows on my hard drive and to use Ubuntu on my USB. My first steps were installing the 16.04.1 ISO using UUI onto a 128 GB USB drive. Once I booted windows 10 into my usb I had the option of 1. Try without install (I chose this) 2. Install Ubuntu (assumed it would install to my main HDD) 3. OEM Install (for manufacturers) 4. Check disc for defects. After I chose option 1 I had a black screen on my screen and the screen led turned to yellow which means there was no input activity. When I turned my computer off and booted into windows everything was slower than usual and my clock was off by 7 hours.

---

### Post by TheFu on 2016-07-27
Welcome to the forums.

The clock thing could be the difference between UTC and your local timezone.  Unix systems are always set to UTC and we choose the timezone to be displayed because they need to support remote users from around the world. I've never touched Win10, so don't know how it deals with time, but suspect this is the issue. Does Windows have a way to use UTC time from the BIOS?

USB performance isn't usually all that great.  One of my Core i5 systems has queuing issues with USB (2 and 3) when more than 2 requests are made. That makes using USB on that machine only useful for backups or streaming media, not an OS.  On newer systems, I haven't seen this issue.

The screen thing tends to be BIOS/GPU specific.  There is a troubleshooting guide just for a "black screen" at boot. Google will find it. Don't know if that will help or not. I've never had that issue ... well, not related to graphics. My issue was related to the TPM HW in the machine.

---

### Post by yancek on 2016-07-27
> My first steps were installing the 16.04.1 ISO using UUI onto a 128 GB USB drive. 

Software such as UUI uses the entire drive regardless of the size of the extracted iso file.  Although it should be possible to use the usb drive and install to another patition it is going to be very complicated and I doubt it will work for you if you are a new user.  Best thing would be to use a small flash drive and UUI to put Ubuntu on it using UUI, boot that and then install to the 128GB drive.  That is, after you get the black screen issue resolved.  Did you see any message or just the black screen?

---

### Post by colemilne54 on 2016-07-27
The time explanation makes sense for it being off.

---

### Post by colemilne54 on 2016-07-27
OK thanks I will try an 4 gig, and the screen was blank and there was no activity going to monitor because it activated sleep mode the 4 gig may fix blank screen I will try and see if that fixes the problem.

---

### Post by oldfred on 2016-07-27
Is system UEFI or BIOS?
Either way you need to partition in advance and use Something Else to install. But what partitions that are required vary between BIOS & UEFI. And if external you can use gpt which is now standard partitioning for UEFI with BIOS where BIOS before only worked with MBR(msdos) partitioning.

       UEFI/gpt partitioning in Advance:
[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu

[/URL]

---

### Post by sudodus on 2016-07-28
It seems to me that the computer boots from your 4 GB USB pendrive, but that it has problems with a driver for some hardware, probably the graphics chip, maybe the wifi chip or something else. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and it will be possible to give more specific help. Until then, please see the following link about the boot option nomodeset (a wild guess assuming you have problems with the graphics),

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

