---
title: "Partition Problem"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by ditane on 2006-03-02
After using the live cd for a few days and backing up my data, I finally went to install Ubuntu.  When I got to the partitioning part, I created one partition that was to become the partition that I installed Ubuntu on. That part gave me no problems. But when I did that, the reamining space changed from reading as "Free Space" to "Unusable"  and it wouldnt let me touch that space.  Something similar happened when I tried to use gparted on the livecd.  It said that I couldn't create any more primary partitions, and I should create an extended partition instead. The only problem was that I couldn't. Any suggestions on what to do? My guess as to why this is happening is this:
I have a Dell with Windows XP. I have to keep Windows XP, because I am required to use it for a few things.  With my Dell, I noticed that it had three partitions already.  One was the main partition with windows (shows as /hda2 from the live cd) and two others. One about 3 GB (i believe /hda1) and another very small (I don't remember what size, but small,   /hda3 i think)  I am pretty sure that these have to do with a dell program that allows me to wipe the drive and reset everything to factory settings without a cd or anything.  I do not want to get rid of these,  because I need to be able to recover Windows for my required things, if it fails (knowing Windows, it will).

Any help would be much appreciated
Thanks

---

### Post by jpkotta on 2006-03-02
You can only have 4 or fewer primary partitions.  If you need more, you have to make one (and only one) of your primaries an extended partition, which can be divided into logical partitions (up to 15, I think).  

If you have all of the reinstall disks from Dell, then why should you need their stupid restore partitions?  You might want to check it out with Dell first, but I bet that they're unnecessary.  If you don't have the reinstall disks, you got cheated.

---

