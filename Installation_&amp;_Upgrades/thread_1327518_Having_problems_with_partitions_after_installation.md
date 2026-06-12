---
title: "Having problems with partitions after installation"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Sportsmaniac1322 on 2009-11-15
I started out with a computer with a 500GB hard drive.  I made 2 even partitions, one for Windows 7 and one for Ubuntu Linux.  I installed Windows 7 on the first partition and that went good, but when I installed Linux on the second partition it split that up in half again.  So right now I have Windows on a 250GB partition, Ubuntu on a 125GB partition, and then another 125GB partition that's not being used for anything.

I'm trying to find a way to combine the Ubuntu partition and the one that's not being used, but I haven't had any luck.  I've tried GParted installed in Linux, and I've even tried the Live CD.  So far I haven't been able to find an option to combine the 2 partitions.  Does anyone know how this can be accomplished?

---

### Post by Sportsmaniac1322 on 2009-11-15
Come on, you're telling me no one has had this problem?  Can someone please help me out?

---

### Post by Bartender on 2009-11-15
Sport -
It's not that nobody's had the problem.  It's more like there are 5.4 million posts that discuss partitioning.
I have no idea why Ubuntu split the existing unallocated space in two.
And there's something missing in your post - there should be at least two Ubuntu partitions, the main OS and a small swap partition.

If it were me, I'd probly boot from a GParted LiveCD (link under my sig) and simply resize the Ubuntu partition all the way over to the end of the HDD.  I'm guessing you'll have to move swap to do that.  You could just delete the swap partition and create a new one at the far right-hand side, apply that change, then resize the main Ubuntu partition.

That would be one way to fix this.  There are others.

---

