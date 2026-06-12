---
title: "GRUB failure &quot;ELF outside core section&quot;, boot-repair-disk doesn't work."
date: 2015-07-03
forum: Installation &amp; Upgrades
---

### Post by george118 on 2015-07-03
Hello,

I dual-boot Windows 7 and Ubuntu 14.0.2. This week, after a shut down from Windows 7 I was unable to boot. When attempting to load GRUB it would fail and restart instead. Running boot-repair-disk then fixed the issue, though there were still errors ( [http://paste.ubuntu.com/11801078/](http://paste.ubuntu.com/11801078/) ).

However, when booting into Windows again, which I hadn't done after the boot repair until today, the initial problem repeated. Running boot-repair-disk again ( [http://paste.ubuntu.com/11817710/](http://paste.ubuntu.com/11817710/) ) and restarting lead to a new message instead "Invalid arch-independent ELF magic".

I'm a massive noob so panicked and attempted to do boot-repair-disk once more ( [http://paste.ubuntu.com/11817761](http://paste.ubuntu.com/11817761) ), and got a THIRD form of error, where GRUB now says: "ELF outside core section".

I'm not sure what's gone wrong at all!

I hope this is in the right forum section...

---

### Post by oldfred on 2015-07-03
ELF errors are often related to grub version issues. Where part of grub was updated but the other part was not.

Are you running some type of RAID?
This looks like RAID, but I do not know about RAID.
/dev/mapper/isw_ddhdbahhgc_WD-WX21A73T3283p1

If useing RAID 0 any corruption on one drive can damage data on both drives.
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

      
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by george118 on 2015-07-03
hello again,

I disabled the RAID 0 caching at startup and now successfully reach GRUB. Booted successfully into Ubuntu! Not tried Windows yet...

What exactly do you think the problem is/was then? Is this something that will stay fixed leaving RAID 0 disabled, or will it be possible to reenable it?

---

### Post by oldfred on 2015-07-03
I do not know about RAID. 
But how grub is installed is usually different. With RAID on, it is installed to the root of the RAID. Without RAID it is installed to the MBR.
And you have to have RAID drivers added to live installer for it to work & mount your RAID partitions. Usually Boot-Repair automatically downloads RAID drivers just in case you have it.

If you have something working I would make sure you have good backups of all your data.

---

### Post by george118 on 2015-07-04
Thanks for the prompting in the thread, everything seems to be working at the moment. :) 

Still not sure exactly what the problem was, nor if it'll happen again, but I think this thread can be closed now.

---

