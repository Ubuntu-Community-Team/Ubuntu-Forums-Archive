---
title: "Partitioning woes"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by DeathRay2K on 2006-08-29
I'm trying to install 6.06 alongside Windows Vista and Windows XP, but the partitioner doesn't seem to be working correctly, or I'm doing something horribly wrong.

When installing, I selected manually edit the partition tables, as I thought since I'd done it with Breezy, I could do it again. Unfortunately, whenever I create the partitions (1GB for swap, 16GB for /, 3GB for /home) and then click continue, they don't show up as possible mount points.
If this weren't distressing enough, when I click back, I see that all three have error mesages, and 'Unknown' filesystems. It doesn't matter what filesystem I use, the problem persists.

---

### Post by catlett on 2006-08-29
Try making your partitions bfore you run the installer with gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) As the name suggests it is gparted but it runs off a live cd. Just download the iso, burn it and boot to it. I have had good results with gparted because it can perform all actions because the hard drive isn't mounted.

---

### Post by randell6564 on 2006-08-30
Have you tryed letting Ubuntu do the partitioning setup?

I'm quite sure that a partition for /home will be left out if you do it that way, but it's really not a big deal unless you really want a seperate partition for /home!

You could also go into your Windows disk manager and format your prospective ubuntu partitions as Fat32, and then start the installation.  Ubuntu will see the vfat and then you could tell her to erase the vfat partitoins and make them ext3.  This worked for me once when I was having similar problems.

Before you do all this though, did you make sure that you specified Exactly where ubuntu is to mount after you created the partitions?  If you fail to do that when using the 'Manual' option, you will not be able to proceed with writing.

---

