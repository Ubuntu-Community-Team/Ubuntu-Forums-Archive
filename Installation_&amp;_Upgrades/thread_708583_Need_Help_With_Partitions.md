---
title: "Need Help With Partitions"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by AbsentHarvest on 2008-02-26
I'm reinstalling Ubuntu.
Better than describing the situation, i'll show you.

[[IMG]http://img90.imageshack.us/img90/8905/screenshotef5.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshotef5.png)

As you can see...
SDA1 is my DELL UTILITY partition.
SDA2 is my Recovery partition for Windows Vista Premium.
SDA3 is my Windows Vista Premium

Everything else is Ubuntu, it's turned out kinda messy, so i'm going to reinstall Ubuntu after i wipe out the petitions.

Is this alright to do?

---

### Post by taurus on 2008-02-26
You don't have to wipe out both /dev/sda6 & /dev/sda7.  Just pick the Manual when you get to the partition part and mount /dev/sda6 as / (instead of /media/sda6 as it showed on the screen) and format it to ext3.  And /dev/sda7 should already be mounted as swap so no need to do anything with it.

---

