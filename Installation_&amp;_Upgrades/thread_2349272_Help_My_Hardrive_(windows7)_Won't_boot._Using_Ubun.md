---
title: "Help: My Hardrive (windows7) Won't boot. Using Ubuntu to fix it?"
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by ghostlander on 2017-01-12
So, I turned on my computer today and after the MSI logo screen it sits  there. I went in to the MSI menu and looked at the loading order, it  says the hardrive is still there BUT, it's not lit up like my external  hardrive or CD drive are when they are plugged in. 

I tried re-plugging the sata and power cords, rebooting, nothing. I'm  thinking maybe something about my windows MBR is not working? 

I'm curious how I can either repair windows, repair the MBR, or maybe  even restore to an earlier point? Using my Ubuntu OS that's working from  a USB stick. 

I would rather not lose everything on my hardrive meaning I need to take the time to back up everything. 


Any help at all would be massively appreciated.

---

### Post by ubfan1 on 2017-01-13
If the BIOS doesn't see the disk as active, the problem is not the MBR -- sounds like a hardware problem.  Are there any BIOS checks to run or maybe discovery of disks?  If you boot from an Ubuntu live-media, and run "try", can you see the disk?  If you mount the disk in an external enclosure, can you see it and does it work?  Some disk failures may be the controller, not the actual disk, so maybe your data is OK, but first time you can access it, do backup.

---

### Post by Autodave on 2017-01-13
As ubfan1 said: the very first time you manage to get into the drive, backup everything!!!!   Can you access the drive through Ubuntu on the USB stick? If so, get everything backed up before going further.

---

