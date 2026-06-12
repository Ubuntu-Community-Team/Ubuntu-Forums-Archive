---
title: "Help on Installing &amp; keeping Windows Data"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by slowy on 2010-07-28
[CENTER][/CENTER]Hello Folks,

I've finally had enough of Windows and have decided to go with Ubuntu. However I hope someone can help me with this query... I currently have a single hard drive which I have partitioned under Windows into two. The old C:\ drive holds software & the windows O/S and the D:\ drive is where I stored photos, documents, etc. Can you tell me if it is possible to install Ubuntu into the old C:\ partition and leave the d:\ partition in tact (for a few weeks to ensure I have backups of everything on here). Alternatively, if I add a new drive and install Ubuntu onto there, will I still be able to access the old D:\ partition (or would I need some kind of dual boot config)?

Thanks in advance for your help!!

---

### Post by McFinnigan on 2010-07-28
I just installed 10.04 onto two of my machines, a laptop with one hard drive and a desktop with 3 hard drives. I can still access all of my data and media while in Ubuntu.

---

### Post by joshedmonds on 2010-07-29
The Ubuntu installer will allow you to select the old Windows partition as the destination of the Ubuntu root (/), but I would recommend two things:
[LIST=1]
[*]Unless need the space and are prepared to reinstall Windows later if necessary, leave it on there. If you haven't been using Ubuntu you may decide to go back, and if you try and sell the computer it will be easier with Windows installed.
[*]Even if you intend to leave the data partition alone, make sure you have a backup of all of the information. Installing an operating system is a process that does entail some risk, even if you are being careful.
[/LIST]

Having said that, I would: 
[LIST=1]
[*]Boot Windows, ensure there is no important data on the C: drive, back up data on D: drive, clean up Windows (uninstall unnecessary programs etc., run a disc check and defrag) and shutdown cleanly.
[*]Boot the live CD and do your partitioning. Resize the Windows partition to 10% greater than the current usage, create a new 10-15Gb ext4 partition for Ubuntu (this can be primary or secondary, a home partition is not necessary but be my guest), and if necessary resize the data partition to fill the rest of the space. Shutdown cleanly.
[*]Boot Windows, and again run a disc check and defrag. Shutdown cleanly.
[*]Install Ubuntu.
[/LIST]

---

### Post by slowy on 2010-07-29
Thanks for the help guys, got it working and can still see the data drive.

---

