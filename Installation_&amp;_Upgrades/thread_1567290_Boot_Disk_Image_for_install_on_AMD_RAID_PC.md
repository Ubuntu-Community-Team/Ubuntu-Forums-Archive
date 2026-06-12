---
title: "Boot Disk Image for install on AMD RAID PC?"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Flasharino on 2010-09-03
[COLOR="Navy"]I tried installing Ubuntu 10.04 WS on my PC but it did not see any disks to install on.  I believe this is because my drives are all configured as RAID.  My mobo is an Asus M3A78-EMH HDMI AM2+ socket with an Athlon 2X 5000+ CPU.  The chipset is AMD 780G.  I have the BIOS configured for RAID drives and I already run Win XP x32 and Win 7 x64 on it.  My boot drive is configured as 'RAID READY' and I have 2 RAID 1 disks consisting of pairs of SATA drives.

From what I have researched it seems that with some tuning it should be possible to install Ubuntu 10.04 but I have little Linux experience and don't want to mess up my existing drives.  I have installed Linux before a few times and run it but never with RAID.

Is anyone aware of an existing disk image that I will be able to install from on my system or would it be possible for someone to create one for me to use?  :p

Thanks.[/COLOR]

---

### Post by Flasharino on 2010-09-07
[COLOR="Navy"]Please reply if you know of a forum or message board visited by people who may have the knowlege and expertise to answer this question.  Thank you.[/COLOR]

---

### Post by ronparent on 2010-09-07
The problem is one that will be fixed in 10.10. Meanwhile, run the install from the live cd. Just before you hit the desktop icon to start the install, open a terminal and run the command: 

> sudo apt-get install kpartx

Installation of kpartx into the session should allow the installer to see your raid partitions. If you have concerns depending on the installer to do the partitioning, you can create the target partition with gparted once kpartx is installed (just remember to leave space for the swap partition). Post if you need more help.

Just a note: if you plan on shrinking a windows Partition (especially win 7) you may want to do that in windows.

---

### Post by Flasharino on 2010-09-08
[COLOR="Navy"]Thank you.  Is there a release date scheduled for v10.10?[/COLOR]

---

### Post by ronparent on 2010-09-08
10/10

Edit: I didn't mean to make my response so curt. 10.10 is maverick meercat and is now in Beta release. The beta looks solid to me and installed flawlessly to my raid 0 (a first). You are cautioned that it is prerelease and has bugs. Usually you are advised to wait a couple of months after the final release to install. If you just want to look at it and play with it a bit, go with it!

---

