---
title: "reinstalling ubuntu partition problems"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by scottie4442 on 2007-01-19
I teach a computer networking degree at a two year college, in this program I teach a UNIX/Linux course in which I use Ubuntu 6.06 to teach Linux with.  All that said to say this, I am having a problem with the computers in my lab, we installed Ubuntu last semester and everything worked fine, this semester the next batch of students are trying to do an install (reinstall actually) and when we get to the part about partitioning the hard drive it is a "no-go".  This is the issue, it will not let anyone remove the sda1 partition, and yes we are running from the LiveCD, I have even tried to do a manual partition, and even gone into Gparted and tried to do the partition by hand, all of these methods are "no-go". I am writing this to see if anyone has any other ides about how to fix this. The last bit of information needed is that these are all SATA drives, setup like this; sda is a windows xp drive (required by the school) and sdb is a Linux drive. Thanks for the help.

---

### Post by scottie4442 on 2007-01-22
OK, an update.  The first week of class is usually nuts so I missed something that one of my students caught.  WHen you are REinstalling Ubuntu, check that the partitions are not mounted, will show a lock in the partition manager, if they are then right click and deactivate them before you do the reinstall.  Sorry for the trouble and hopefully this will help the community. (FOrgot the KISS principle, Keep It Simple Stupid, tried to look for something tough)

Scott Adams

---

### Post by scrooge_74 on 2007-01-22
I think it helps to have options to get replies to problems or to get fresh ideas

---

