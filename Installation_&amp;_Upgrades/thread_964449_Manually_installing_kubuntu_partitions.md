---
title: "Manually installing kubuntu partitions"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by HH60Gunner on 2008-10-30
Hi,

I'm trying to install kubuntu on my system and I've previously had open suse and xp dual booted.  I decided that I wanted to try kubuntu 8.10 in place of suse.  However when I try to install kubuntu there's no option to automatically put kubuntu in place of suse.  So I need to manually delete and create partitions for kubuntu.  However I'm still new to linux and am not sure what I need to do for partitions.  Any help would be appreciated.  After deleting suse I will have 160G free on my system.  What is the best approach to partitioning my system?

---

### Post by Sef on 2008-10-30
If you would install Kubuntu, there is a partitioner on it.   You would need to manually partition the hard drive.  It would allow you to delete the Suse partition, then reset up the partition, then reformat that partition.   It is not hard, but the first time can be intimidating.

---

### Post by Partyboi2 on 2008-10-30
Delete your suse partitions then start the installer and when you get to the partitioning stage choose "manual" and create a / (root) (ext3) partition say about 20-30 gig and set the mount point to / then create another partition for swap (about x2 amount of ram but would not suggest more then 3 gig) then create another partition for /home (ext3) and use the remaining space for this partition setting the mount point to /home.

---

### Post by heman22union on 2008-10-31
Here is a link to what the partition screen is going to look like. [http://ubuntuforums.org/showthread.php?t=962234](http://ubuntuforums.org/showthread.php?t=962234)
Scroll down to the bottom and you'll see the way I set up my partitions. Its just an example/visual aid hope it helps and goodluck.

---

