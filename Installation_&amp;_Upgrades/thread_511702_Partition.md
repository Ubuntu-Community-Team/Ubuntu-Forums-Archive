---
title: "Partition"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by newtonrealman on 2007-07-28
Hello!
I have windows currently installed and i was excited to give ubuntu a try.
I then started ubuntu installation and when it asked about partition i set it up to 30%.
After the installation I realised that actually my windows has 30% and ubuntu has 70% but i wanted it the other way round. How can i fix this problem?
If i've got to remove the linux and install it again.. how do i remove it? Just by deleting the partition?
Thanks,
Newton

---

### Post by chewearn on 2007-07-28
You can use a partition manager to resize the partitions.  One way is to use a commercial Windows software e.g. Partition Magic; another way is to use the free GParted LiveCD.

Ubuntu actually comes with GParted, which you can install via Synaptics, but the problem is, you can't resize your Ubuntu partition while it is being mounted (i.e. while Ubuntu is running.

To get around this situation, I usually use the GParted LiveCD.  Download the iso image here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Burn the iso into a disc, and boot from it (just like when you boot Ubuntu LiveCD).  Using the GParted program should be simple enough, and quite similar to commercial software like Partition Magic.

---

