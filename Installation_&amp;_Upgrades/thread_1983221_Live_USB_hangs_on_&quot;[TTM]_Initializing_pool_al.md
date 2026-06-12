---
title: "Live USB hangs on &quot;[TTM] Initializing pool allocator.&quot;"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by Russiat on 2012-05-19
Hello --

     First let me apologize in advance if this has been posted before, but several searches didn't yield any satisfactory results. Also, this doesn't technically have to do with "installing" Ubuntu, but I thought that it was close enough.

Today I've been trying to set up a USB flash drive (SanDisk 16gb) as a Live USB for Ubuntu 12.04. I have already run the U3 remover tool provided by SanDisk as suggested in many places I've found while trying to solve my issue, I've formatted my flash drive several different times in the process of preparing a Live USB, both with NTFS and with Fat32, and I've tried a number of different things. The problem persists.

The problem is that when I boot from USB (my PC actually recognizes the flash drive as a hard drive, so instead of changing the boot priority to USB, I change the hard disk boot priority to SanDisk) and select "Run Ubuntu using this USB Device" (or whatever it says exactly), the operating system starts booting up, but then hangs on a line saying "[TTM] Initializing pool allocator."
I've left my computer on stuck on this screen for about an hour or so now, and this is the fifth or sixth time I've tried to boot and it's come to this, so I don't think that just waiting for it is going to work.

I prepared the USB using the PenDriveLinux software provided on the Ubuntu website. The operating system I'm currently running (and the one I used to prepare the USB) is Windows 7 Professional 64bit.
My computer hard ware is the following:
RAM: 4GB DDR3
Graphics Card: NVidia GeForce 460 GTX
Processor: AMD Phenom II X4 Quad-Core 3.2GHz
Power Supply: Apevia Java Power 650watt
Motherboard: Gigabyte 890GPA-UD3H

If it makes any difference, Windows is installed on a 64gb Solid State Drive, but the files that I used to prepare the USB were on a separate 2TB mechanical drive.

If you need any more information please tell me.

EDIT: I just tried re-preparing the USB with UNetbootin, and this time I encountered a different problem. When it brought me to UNetbootin's menu, I selected "Try Ubuntu without installing it," and the screen went black, and the caps lock and scroll lock lights on my keyboard started blinking on and off. Nothing else happened.

---

### Post by Russiat on 2012-05-19
Haha, I just realized that this thread would be more accurately placed in "Absolute Beginner Talk," considering I have very, very minimal experience with Ubuntu, and Linux in general. If a mod wants to move this over there, I won't be offended.

---

### Post by 2F4U on 2012-05-20
First of all, did you verify the checksum of the downloaded iso file? If not, 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The second attempt with unetbootin sounds like a bad "burn". This sometimes happens due to circumstances unknown to me. I had it myself and it often worked on a second or third attempt.

---

### Post by Russiat on 2012-05-20
I verified the checksum, re-prepared the USB with PenDrive Linux' software, and tried again. It gave me a different problem this time, yet again:
It hangs on something along the lines of:
[     5.015694] [drm] nouveau 0000:01:00.0: EvoCh 0 Mthd 0x0018 Data 0x20000048 (0x10000x03)

The only thing is that every time I try to boot, it hangs on something similar to that, except some of the numbers and what not are different.
I even tried preparing a different USB drive I had (4gb Kingston), and got the same problem.

---

### Post by gordintoronto on 2012-05-20
This is a possibility: use "nomodeset," as follows.

To boot, hold shift from the BIOS boot to get a Grub menu. Press "e" on getting the Grub menu. Using the arrow keys, navigate to, and delete, quiet and splash and type the word nomodeset in their place. Press Ctrl-x to boot.

Your graphics card is not well supported in the current Linux. There's a way to fix this on an installed or persistent system, but first you need to be able to boot a working system.

---

### Post by Russiat on 2012-05-20
Thank you, gordintoronto. I'll screenshot this and follow it to a T in just a minute, and then edit this post with the results. Hopefully the edit will be done from within Ubuntu.
When you say that my graphics card is not well supported in the current Linux, do you mean the specific model NVidia GeForce 460 GTX, or are there several NVidia cards that are unsupported?

EDIT: I just tried using the method you just gave me. The first time I tried booting, the screen told me that it was trying to start Grub, but then it gave me an "unknown file system" error and put me into grub rescue. The file system on the USB device is Fat32; does it need to be formatted for, say, Ext2 or some other file system? If so, how would I go about formatting it for such a file system and then preparing the USB as an Ubuntu Live USB within Windows?

Every time I tried booting while holding shift after that first time (I'm not sure what I was doing differently, but I never got back to that screen), I got to a screen saying:
SYSLINUX 4.06 EDD 4.06-pre1 Copyright (C) 1994-2011 H. Peter Anvin et all
boot:

And no matter what I typed into "boot: " it would say that it could find no such kernel or something similar. If I did nothing and left it at that screen for more than a few seconds, I was brought to the Ubuntu menu, where I could select "Try Ubuntu Without Installing" and everything else.

---

### Post by gordintoronto on 2012-05-20
So pressing e didn't take you to a screen where you could edit the boot parameters? [Puzzled look]

Fat32 is a good file system for USB flash drives.

And "Try Ubuntu Without Installing" got you nowhere?

BTW, I've had very good success using Pendrivelinux. I usually create a small flash drive with no persistence, then use that to install onto a larger flash drive. (I fool around with a lot of Linux distros/versions.) At this moment I'm actually running from an 8 GB flash drive which has Ubuntu 12.04 *installed* on it.

The 400 series Nvidia cards may not be "well supported." They work perfectly as generic video cards, but might not support some features of Ubuntu. It's very odd; I have a 9400 GT, which almost certainly cost less than your video card, and isn't any older, but it's "well supported." One difference is that computers based on the Atom Ion use 9400 GT built-in video, and there are lots of them out there.

---

### Post by Russiat on 2012-05-20
So you have no idea why it's giving me an unrecognizable file system error?
Then I suppose for now I'll go Linux-less until someone else comes up with an idea.

---

### Post by Russiat on 2012-05-26
Just making a last attempt bump to see if anyone has a solution...

---

