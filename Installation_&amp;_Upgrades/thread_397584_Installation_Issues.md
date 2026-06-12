---
title: "Installation Issues"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by LoneStarSamurai on 2007-03-30
To any and all --

I am installing Ubuntu 6.10 on a dual boot system (Win XP on the other partition, on a Core 2 Duo 2.18 gB chipset, Intel 96x series board), and am running into issues. I boot into the Ubuntu installation, and am going through repartitioning the secondary partition when all hell breaks loose.

I've blown the partition to reallocate the space, and then set up my partitions for ext3 and one for swap. All processes appear to work, and I don't get any errors there. I click Forward, and it asks to set my mount points. I set the points I want, on the appropriate segments, only to be informed that there is not a root filesystem in place. I click Back, and the info flags say that the partitions newly created do not have a recognizable format or are perhaps damaged.

So what gives? How am I supposed to proceed? Out of curiosity, when setting up the partitions, I do believe it asks only whether it's ext3 or swap, so theoretically, any ext3 type partition should be able to be assigned however I want (/, /var, etc) right?

So what do I do? Someone, please...help!

---

### Post by mac.ryan on 2007-03-30
It might be a totally different issue than the one I experienced, however, I experienced a number of similar problems with an external USB disk. It looked like some "old data" where interfering with the creation of new partitions.

In my case, I worked it around creating a new partition (NTFS) from windows, **and formatting it**; then, when I got back to the ubuntu LiveCD, I erased it and created the ext3 and swap ones... and it worked.

Again, your issue might be different... but the symptoms look similar.

If you can't work it around this way, it might be helpful to know what kind of HD you are working with (SATA? SCSI? USB?), if it is master or slave, if you have other HDs installed, etc, etc...

Best luck!

---

### Post by LoneStarSamurai on 2007-03-30
I'll try that at the next chance. And just as an fyi, it's a 250gb sata drive. Thanks!
Suggestions...keep em coming!

---

