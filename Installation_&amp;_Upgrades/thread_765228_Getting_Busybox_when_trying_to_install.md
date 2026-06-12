---
title: "Getting Busybox when trying to install"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by 54lzy on 2008-04-24
I'm trying to boot the Hardy live cd to install, but whenever I try, it shows the loading bar and then when it should be loaded it shows busybox.  I thought it may have been my gfx card so i switched to the onboard which didn't help and I also disconnected my hd to see if it would just boot.  Any ideas guys?  Thanks in advance!

---

### Post by encompass on 2008-04-24
You just burned the CD, have you "checked the CD for defects"... it's built into the CD.  You may find an error there, which means it's a misburn.  It would also be good to give us your system information and if you have run linux on this computer before.

---

### Post by matl1984 on 2008-04-24
see [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195) for my solution.

change "sata mode" in bios from "ahci" to "raid"

---

### Post by 54lzy on 2008-04-24
no defects and its just a compaq so i cant do that in bios its never ran linux before up until an hour or two ago i just installed Wubi.  radeon x800 GTO 2 gigs of ram sata hard drive amd 3500+... any ideas?  Thanks

---

### Post by 54lzy on 2008-04-24
bump, PLZ HaLP

---

### Post by dalesyk on 2008-04-25
> **54lzy said:**
> I'm trying to boot the Hardy live cd to install, but whenever I try, it shows the loading bar and then when it should be loaded it shows busybox.  I thought it may have been my gfx card so i switched to the onboard which didn't help and I also disconnected my hd to see if it would just boot.  Any ideas guys?  Thanks in advance!

I'm seeing the same issue with both x32 and x64 8.04 desktop cd's.  I verified my x64 cd (on another system) and it matches the md5 from kernel.org where I downloaded it.  When either cd boots, I see the boot choices for 1 or 2 seconds and then a language dialog fills the screen and I see a 30sec timer count down to the left.  I choose English, hit enter and then down arrow to install option and enter to launch.  I get the knight rider progress bar and Ubuntu logo for a few seconds and then drop into a busybox shell (that shows initramfs prompt).  I tried the verify cd option and get the same issue.  I haven't played with bios settings, but this is an older amd 939 system that works fine with centos, knoppix, sme server, etc.  If hardware info is needed, I can send lspci output from knoppix or anything else useful.

Thanks,
Dale

FYI - I noticed this bug as #222176 on bugs.launpad.net

---

### Post by rondackcpu on 2008-04-25
Hi, folks,

I've had this busybox problem with all the downloads for the last 6 months.  Somewhere I read that the solution is to press F6 for more options before accepting the offer to "try Ubuntu on your machine".  Type in as a new option < irqpoll > and proceed with the "try" offer.  I have no idea what this means or does, but it has been the only way I can boot any new downloads.  (Without the < >, of course.)

Better luck with this thought!

CRS

---

### Post by tparker on 2008-04-25
> **54lzy said:**
> I'm trying to boot the Hardy live cd to install, but whenever I try, it shows the loading bar and then when it should be loaded it shows busybox. 

If you have a floppy drive in the computer, put a blank floppy disk in it then try the install again. You won't have to do anything with the disk, just leave it in. I had this same error and a google search turned up someone with the floppy suggestion. If yours is the same problem it seems that something in the install really wants to find a floppy, maybe a throwback to the floppy boot disks everyone used to make as part of an new install, I don't' know, but this worked for me.

---

### Post by encompass on 2008-04-26
Personally, at this point, I would search for and file a bug with ubuntu.  No need for you to really look for a work around after this much effort.  The only think I could see you do that you haven't is update your bios.  Which I would do, and if that doesn't help, file the bug.

---

