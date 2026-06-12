---
title: "Dual boot Questions"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by SliderTech on 2011-11-18
I am going to do a clean install with Win7 and Ubuntu on my XPS system.

Any suggestions would be gratefully appreciated.

I am not an experienced Ubuntu user.  


Should I install 7 first then Ubuntu? 

  
Thank you.

---

### Post by BillyBoa on 2011-11-18
Go here and follow the instructions.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


If you have any question, post it here

* Of course start from Win installation.

---

### Post by Mark Phelps on 2011-11-21
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by SliderTech on 2011-11-23
I just bought a new 1T HD I will use for a clean install and then I can move files over later from this drive. 

By the comment by BillyBoa, I should start with windows first.  

Ill follow the link instructions. 


Thank you guys and ill start this on the weekend.  Ill post back here if any problems or questions then Ill close this thread when all is said and done.

Thank you.

---

### Post by SliderTech on 2012-05-29
I just wanted to say thanks for the advice.

I have been gone for a while so I never had a chance to make my change.  I returned home a few days ago and will make the change soon.

Thanks

---

