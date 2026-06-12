---
title: "Installation freezes"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by HighCorral on 2008-05-09
I have been struggling to install Ubuntu 32-bit over Vista.

I boot from CD, Select my language and Install, then I get the splash screen for a little while until it stops and the disc stops spinning.  A few minutes later the splash screen disappears leaving this:

[img]http://www.widgetbuilding.com/uploads/forum/ubuntu.jpg[/img]

I have tried numerous times all to no avail.
-- I checked the memory (ok)
-- I checked the CD (ok)
-- I tried installing CentOS 5.1 and it crashed as well.

Here is the text from trying to install CentOS
[img]http://www.widgetbuilding.com/uploads/forum/centos.jpg[/img]

I don't even know where to begin.

Acer Aspire T690
Intel(R) Core(TM)2 CPU 4400 @ 2.00GHz 2.00GHz
2038 MB
32-bit OS

I don't have the BIOS info handy.

---

### Post by Pumalite on 2008-05-09
Do memtest. Check your drive with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Check all your cables and connections. Update your BIOS. Check your power supply.
Did you do md5sum?

---

### Post by housam on 2008-05-09
Do format your HDD manually using Gparted tool (on the live cd or [[COLOR="Red"]_download_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") and burn it to a cd to get a live cd of it ) then create the needed partitions and do the installation.

---

### Post by HighCorral on 2008-05-09
> **Pumalite said:**
> Do memtest. Check your drive with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Check all your cables and connections. Update your BIOS. Check your power supply.
Did you do md5sum?

-- I selected the memtest option on the ubuntu iso and it was ok.
-- I also checked the media.

What I find interesting is that both distros failed: ubuntu and centos.  I could not install either one.

And I did install centos on another PC using the same discs.
I'll update the BIOS.

---

### Post by Pumalite on 2008-05-09
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
The use Gparted Live CD and make your partitions. I would still use TestDisk first.

---

### Post by HighCorral on 2008-05-09
> **Pumalite said:**
> DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
The use Gparted Live CD and make your partitions. I would still use TestDisk first.


Why dban?  Can't I just install linux right on top of vista?  I just tried to install ubuntu again, this time with "nospash" (F6) to see the messages.  Pretty much the same thing as in the pictures above.

---

### Post by Pumalite on 2008-05-09
That's right; after Micro%&$, DBan.

---

### Post by HighCorral on 2008-05-09
> **Pumalite said:**
> That's right; after Micro%&$, DBan.

I appreciate the help and suggestions however I would like to understand the reasoning behind it.

The linux install locks up on my PC.  How will wiping my disk with dban affect this?

---

### Post by cferrell on 2008-05-09
I'm getting the exact same problem. I've been trying to get linux install for several weeks now. The problems started when I tried to find a free partition manager that could resize my partition (I didn't know about NTFSresize or Gparted), and I think one of the programs that I tried (which of course didn't work because I had to buy the full version) screwed with my bootup. Now, not a single linux distro works, i've probably tried 5 or 6. Unfortunately, I don't have my windows cd on me (im at college), so I don't want to nuke my hard drive without it. Any thoughts?

By the way, linux live cd's worked great before that **** screwed with my computer, I was trying out different distros to find the one i liked most. This crap has been pissing me off for weeks now.

---

### Post by HighCorral on 2008-05-09
> **cferrell said:**
> I'm getting the exact same problem. I've been trying to get linux install for several weeks now. The problems started when I tried to find a free partition manager that could resize my partition (I didn't know about NTFSresize or Gparted), and I think one of the programs that I tried (which of course didn't work because I had to buy the full version) screwed with my bootup. Now, not a single linux distro works, i've probably tried 5 or 6. Unfortunately, I don't have my windows cd on me (im at college), so I don't want to nuke my hard drive without it. Any thoughts?

By the way, linux live cd's worked great before that **** screwed with my computer, I was trying out different distros to find the one i liked most. This crap has been pissing me off for weeks now.

Well, during this process something happened to my Vista installation and I can no longer boot to Windows.  The Windows Repair states it is unrecoverable.

---

### Post by HighCorral on 2008-05-10
I downloaded the Alternate install ISO and tried it out.  I wasn't sure how to partition the drive...so I muddled through it.

Then it looked like it was ready to start installing and it gave a bootloader error.  The screen was red.

---

### Post by HighCorral on 2008-05-10
I burned the [gparted](http://gparted.sourceforge.net/index.php) live cd iso 0.3.6-7

Ran it in "failsafe mode" and it crashed as well with a segmentation fault.

Memory?
Harddrive?
CD Drive?

[img]http://www.widgetbuilding.com/uploads/forum/gparted-live-0.3.6-7.JPG[/img]

I am currently running Memtest86+ v2.01.

---

### Post by HighCorral on 2008-05-10
A [suggestion from the Bodybuilding.com Forum](http://forum.bodybuilding.com/showthread.php?p=164216181#post164216181) was that the problem might be related to the dual-monitor video card I had installed.

Sure enough, when I removed the card I was able to install ubuntu without a hitch.

But...after the install I put the card back in and it froze again.  So I cannot use the card, apparently.  I tried coming up in Safe mode (which it does) but I cannot get to the GUI.

Nvidia GeForce FX 5200

---

