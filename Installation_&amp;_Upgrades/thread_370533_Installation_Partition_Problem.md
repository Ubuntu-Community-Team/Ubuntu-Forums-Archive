---
title: "Installation Partition Problem"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by MikeBrandman on 2007-02-25
I'm having a problem with the partitioning of my hard drive.
I am planning on putting ubuntu on half of my 250GB external drive so I can use the other half on my XP system.  I partitioned it into 114 and 116 (for some reason it doesn't have a full 250) using partition magic on XP.
When asked where to install to, I am given the options of my 80gb internal, my 250gb external, largest continuous, or manually edit partition.  I go into the 250gb and am presented with erase entire disk, largest continuous, or manually edit partition table.
Since I don't want to erase the entire disk, I go into the partition table.
I hit forward after the chart and I filled it out like this:
[http://img508.imageshack.us/my.php?image=screenshotje1.png](http://img508.imageshack.us/my.php?image=screenshotje1.png)

I keep getting an error saying I don't have a root directory.  

Is there any way I can get it to recognize the 114gb or 116gb partitions or fix that root error?

---

### Post by eapache on 2007-02-25
This is a really annoying bug, but it is really simple to fix. For some reason, ubuntu won't "recognize" partitions not created by its own disk formatter, so you have to delete and recreate the linux partitions (root and swap) from with the ubuntu installer partition manager. It should work fine after that.

---

### Post by rsambuca on 2007-02-25
You can also change the instructions in the ubiquity installer by [[COLOR="Red"]following these commands[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1700787&postcount=29")

---

