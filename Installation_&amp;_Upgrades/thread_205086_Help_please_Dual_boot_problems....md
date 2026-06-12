---
title: "Help please? Dual boot problems..."
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by EhtOtam on 2006-06-27
Hello I just installed Ubuntu Dapper on my computer, I was hoping to dual boot with XP but for some reason it did not exactly work the way I planned.

Here is what I've got going on, I have two hard drives on my system, an IDE IBM 80gb drive as my windows drive, and a SCSI/RAID Seagate 300gb drive which I installed Ubuntu onto. Now the problem I'm having is that for my computer to recognise my IBM 80gb drive's full size I had to use the IBM boot manager. Now when I booted from the Live CD and installed Ubuntu on the SCSI/RAID drive, after installing it completely ignored my boot manager for the IBM drive and will not allow my IBM drive to even run. So in effect I cannot boot into windows anymore. Grub would not even recognise that the manager is even present. 

I'm fairly new with linux and Grub things I'm learning so you will have to be basic with me, anyway I want to know how I can get Grub to at least Dual Boot my manager so that I can load windows again.

Thanks

Nathaneal

---

### Post by beausimon on 2006-06-27
I think that's similar problem to mine. The liveCD installer overwrites the MBR, which also happens to be where your IBM boot manager is. If it was a regular Windows XP MBR, boot up the Windows XP CD, go to repair console and do a fixmbr. Not sure if IBM boot manager can be similarly repaired.

---

### Post by EhtOtam on 2006-06-28
Problem was resolved, I just went into the grub folder and edited the menu.lst file by  adding the code to direct it to my windows hard drive. Thanks for looking though...

Eht

---

