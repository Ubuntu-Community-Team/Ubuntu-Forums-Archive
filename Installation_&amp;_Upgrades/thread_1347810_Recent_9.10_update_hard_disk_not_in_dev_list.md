---
title: "Recent 9.10 update hard disk not in /dev list"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by SuperDaveUMO on 2009-12-06
I have an Intel 64Bit machine with 2GB of RAM, 1 640GB hard disk and 2 identical 1.5TB disks.

I am using Ubuntu 9.10 64Bit Alternate (I am going to use software RAID).  When I install the OS fresh (no updates or installs), I see all three drives in the partitioner during install.  I install Ubuntu to the 640GB (formatting to Ext4) and reboot.  All goes well and I see all three drives under "Places".  Of course the update manager comes up.  I update everything (no additional repos or sources were added) and reboot.  Now, it boots up off the 640GB drive just like before but recognizes only ONE 1.5TB drive!

I look in /dev and where there used to be /sda /sdb and /sdc there is only /sda and /sdb.  /sdc is completely missing.  If I boot into the live CD again, all three drives are there as well as if I boot into GParted.

Just as a note, all three drives are formatted with Ext4.  With a fresh install (no updates), I can access all three drives.

I'm pretty sure this is from an official update that has happened in the last two weeks as I had this system running with all three drives up until very recently (last two weeks or so).

Any help with either the update issue or how to get my /dev/sdc drive back would be very appreciated.  Thanks!

---

### Post by xrizz on 2009-12-06
I think I am experiencing the same issue with 8.04 64 bit and the kernel update that ran this week. Everything was going well up until this weeks update, now I can't detect my SATA drives connected to southbridge. I'm wondering if this is hardware related...

Chris

---

### Post by SuperDaveUMO on 2009-12-06
If I were a betting man, I'd say this was a software bug that was introduced in the latest updates.  If it were hardware, then I wouldn't be able to See everything during a fresh install (no updates).  If you can, you might try that; a fresh install with 8.04.  If you get your drives back, then you know it's the update.

---

### Post by SuperDaveUMO on 2009-12-08
I decided to give your thought a try.  I have 6 SATA channels on my motherboard and I am only using 3.  I have never had a problem with the 640GB so I didn't touch that one.  I moved both the 1.5TB drives to other unused channels.

I updated and, voila, it works!  But I did notice there were more updates this time around.  So I can't be absolutely sure it was a hardware thing or if there was a new update that resolved this issue.

---

