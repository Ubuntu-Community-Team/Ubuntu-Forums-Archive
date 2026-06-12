---
title: "HP Recovery and Ubuntu"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by AlexParky on 2008-08-30
Hey Everyone,

I'm using an HP DV9000 laptop - it came with my main harddrive (the one that held the Vista operating system), a data harddrive (just and 80 gig free space) and a small HP recovery drive. Since then, I've installed Ubuntu on the extra Data drive. Now I'm thinking to use HP recovery to start Windows Vista all over again - my question is this. Will I lose Ubuntu on the extra harddrive as a result of using HP recovery? Worse still, will Ubuntu's presence destroy the recovery and inadvertently destroy my computer as a whole? 

From windows, I cannot see the D: Drive Ubuntu is on, but I can see my recovery and main harddrive. But in Ubuntu I can see all the harddrives.

Ideally I'd like to keep Ubuntu on the data drive. It's a useful alternative and gives me piece of mind in case Vista packs up one day on me. I don't need the data drive, since I have an external harddrive.

Thanks, guys!

---

### Post by JimmyBEng on 2008-09-24
My experience with HP Recovery:
I got a dv9500 last october.  After booting into vista once, I decided I didn't want to dual boot and completely switched to ubuntu.  I completely deleted vista and the recovery partition.

Long story short a month later i considered dual booting vista and ubuntu.  I had a system recovery DVD whose sole purpose in life seemed to be to recreate the recovery partition.  However, after trying to reinstall vista from this partition failed completely.  I tried several times and it always failed.

This may just be a problem with the DVD, the partition could work better.(?)

Also other windows recovery/install disks I have used, tend to ignore linux partitions and just focus on the windows ones.

My advice, just backup everything, then give it a shot.  Worst case is that you have to re-install an OS or two right :)

Hope this helps.

---

### Post by cariboo on 2008-09-24
Using the recovery utility may over write the mbr, if it does you can use the livecd to restore grub. If this happens just use Google to find a thread on restoring grub, it has be covered so many times that you should get more links than you have time to look at.

Jim

---

