---
title: "Cannot install Ubuntu - no root partition"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by Tratz on 2012-03-22
Hey Folks,

I can't seem to install Ubuntu 10.04, 11.04 or 11.10. I've tried swapping out thumb drives, changing the SATA emulation from RAID to IDE/ACHI. I used GParted to pre-prepare my extended linux partition. No matter what, it seems the installer refuses to see any of my hard drive partitions. If I run it off the live CD, I can access all of said partitions. My Windows 7 partition runs without a hitch.

Attached are some screens and my DXDiag. I'm running out of ideas personally. I may try a different Linux distro altogether...see if I have any luck. Thanks in advance.

---

### Post by darkod on 2012-03-22
You need to check in windows Disk Management whether the disk is Basic or Dynamic. It should be Basic, ubuntu doesn't understand dynamic disks because that is MS format.

If it's basic, another possible issue is raid meta data remains if the disk has been used in raid before. The meta data stays there even after formatting. Windows ignores it but ubuntu doesn't. So it doesn't show the partitions during install.

If this is your problem, and ONLY IF NOT RUNNING RAID, in live mode in terminal do:
sudo dmraid -E -r /dev/sda

Confirm to remove the meta data and off you go.

---

### Post by Tratz on 2012-03-24
This is going to sound really stupid...but I can't tell with any certainly how involved RAID is. This is an off the shelf HP computer with *one* 2TB hard drive...when I check the BIOS settings, the SATA Emulation is set to RAID. If I change it to ACHI, the Windows 7 partition won't boot...it blue-screens part way through. I checked the RAID configuration and saw one volume with 2 partitions...1 of which was for HP recovery. 

Disk Management showed partitions were not dynamic, but basic instead. So I guess the big question is - why the heck would my BIOS have SATA RAID emulation enabled and will it break my Windows partition if I remove the meta-data. I may have to contact HP support on this one. If anyone here has any idea, let me know.

---

### Post by mastablasta on 2012-03-24
> **Tratz said:**
> 
  I may have to contact HP support on this one. If anyone here has any idea, let me know.

a good idea. 

BTW how can only 1 disk be RAID? you need to have at least two disks to have RAID as i understand it. Otherwise it is just pointless. RAID is used so that in even that one disk fails you can simply replace it and data will be copied/restored from second disk

---

### Post by Tratz on 2012-03-24
> **mastablasta said:**
> a good idea. 
 
BTW how can only 1 disk be RAID? you need to have at least two disks to have RAID as i understand it. Otherwise it is just pointless. RAID is used so that in even that one disk fails you can simply replace it and data will be copied/restored from second disk
 
My point exactly. Where's the redundant array with one hard disk? Nevertheless, my BIOS, Windows 7 and seemingly the Ubuntu installer behave like *something* RAID related may be going on. I'll post back once I get a hold of HP.

---

### Post by oldfred on 2012-03-24
If your Windows 7 was never in ACHI mode you have to update it first before changing in BIOS.

BIOS change ACHI mode & Vista/7 does not boot.
[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

---

