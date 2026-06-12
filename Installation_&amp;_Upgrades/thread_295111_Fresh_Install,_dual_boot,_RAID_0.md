---
title: "Fresh Install, dual boot, RAID 0"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by dboot on 2006-11-07
Hello,

I convinced a friend who worked (as an intern) for M$ to try out Ubuntu. After showing him Beryl and some programs I use, he wanted to dual boot. I thought I would be able to simply repartition his HD and have him using Ubuntu in no time. After several failed attempts, I told him to let me know the next that he's going to re-install Windows so I can help him install Ubuntu.

His two identical hard drives came with Windows installed in RAID 0. Neither the install CD nor the alternate CD recognizes his two harddrives as a single partition. 

Is there another way for Ubuntu to recognize his harddrives as a single partition? The longer it takes me to install Ubuntu, the less my friend wants it on his computer (he truly is in love with Microsoft).

Thanks!

---

### Post by ethan961 on 2006-11-07
Try the GParted live cd, it has a newer and better partitioner. It should also list them as two seperate devices, and show the partitions on each hdd.
Ethan

---

### Post by dboot on 2006-11-08
Maybe I'm confused...Shouldn't Ubuntu recognize the two raided harddrives as one harddrive so the Linux partition will be raided too?

I haven't tried GParted, thanks for the tip!

---

### Post by wkulecz on 2006-11-08
A windows raid setup is probably "fakeraid".  Unless you can find Linux drivers for the raid controller you are out of luck.  If you can find the drivers you'll be setting up dmraid instead of using mdadm, so search for dmraid setup howtos.

Add a third drive and install Ubuntu to it,  anything else is not ready for prime time yet.

--wally.

---

### Post by dboot on 2006-11-08
Thanks for the clarification, wally.

---

### Post by nyinge on 2006-11-09
I got mine successfully installed as a dual boot with [this guide]("https://help.ubuntu.com/community/FakeRaidHowto").  It takes a bit of reading as it carefully explains the steps.  Pay attention to the troubleshooting part though.

The guide only applies to software raid (fakeraid); usually it is the one that comes with the motherboard.

---

### Post by wkulecz on 2006-11-09
> **nyinge said:**
> I got mine successfully installed as a dual boot with [this guide]("https://help.ubuntu.com/community/FakeRaidHowto").  It takes a bit of reading as it carefully explains the steps.  Pay attention to the troubleshooting part though.

The guide only applies to software raid (fakeraid); usually it is the one that comes with the motherboard.

Raid is difficult enough without confusion over the the names of the two major "schemes".  Windows raid (NVraid, Silicon Image Medley, Intel's SATA raid, etc) are what Linux calls "fakeraid".  Real hardware raid is expensive.  Fake raid acts like hardware raid by making the raid appear to be a single drive to the OS with the work done in the driver that gets installed.  Its really "software raid" too if there is no hardware support for calculating and writing the parity for raid5 which for sure is the situation if it came "free" with the MB.  On Linux if you can find the "raid drivers" for your hardware you can setup and install with mdraid.  IMHO the only reason to do this is to share a raid array with Windows.

"Normal" Linux raid is now "software raid" and uses the mdadm tool.  Multiple /dev/hdaX /dev/hdcX /dev/sdaX devices are "assembled" into the array by the md subsystem and is used like a normal device but as /dev/md0 instead of /dev/hdb1 or whatever.

Benchmarks I've seen between "software raid" "fakeraid" and expensive hardware raid boards really only showed significant differences for raid5, if the improvement is "cost effective" or not is another issue, but for me the clear answer was no.

Linux drivers for real hardware raid boards are pretty scarce.  "fakeraid" (dmraid) and "software raid" (mdadm) are setup quit differently.  Pick your strategy and read up on it before starting.  As I said, mdadm is probably the best way to go if you don't need to share a raid array with Windows, in which case you are out of luck if you can't find Windows drivers for your "fakeraid" chipset.

There be bugs here, neither are really ready for prime time IMHO. Use the search on my name, adding a raid5 array to my raid1 install broke the system so it wouldn't boot.  Wasn't too hard to figure out and fix (but note the total lack of help!), but while raid1 or raid5 is supposed to improve data integretity, but my experience is it increases system fragility.  Thus if you aren't comfortable booting into a minimal system and using the command line to do potentially irreversible operations, I'd suggest you forget about raid on Ubuntu for the time being.  Use the second drive to run rsync from a cron job everynight to keep your system backed up.

--wally.

---

