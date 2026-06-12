---
title: "Anybody here live within 100 miles of Vancouver, B.C.?"
date: 2024-11-05
forum: Installation &amp; Upgrades
---

### Post by rudy5 on 2024-11-05
.. . and would be interested in taking on a data rescue mission? Home folder stuck on a broken Dell/Ubuntu 18.04 system. Can't seem to be able to copy the home folder to an external drive. 
Can someone help rescue my almost 20 years' worth of data, and copy it to a fresh Ubuntu 22.04 install on the same Dell XPS 9360?

---

### Post by yancek on 2024-11-05
You are over a year late installing a current version of Ubuntu but can you still boot 18.04?  Or are you only able to boot 22.04 from a usb?  Is it just the /home partition you a are having problems with?  When you try to access it do you get an warning/error message?  If so, what are they?  What exactly does 'stuck' mean.  Does the computer freeze/ stop responding?  How are you trying to copy, using some drag/drop method. cp command from a terminal.  More details needed.  Did you have a separate /home partition for 18.04?  Do you have a separate /home partition for 22.04?  Try running the command below which will list partitions and POST THE OUTPUT here.  Identify which partition is the problem partition.

> sudo parted -l

---

### Post by rudy5 on 2024-11-07
Hi Yancek,
(Let me preface this by saying that I'M OUT OF MY DEPTH HERE, and would like nothing better to have found someone who could put their own hands on my computer.)
Many questions here that I've already responded to in separate forum threads --- still learning how to use this forum properly, among many other thngs!
Quickly, I've been on a Dell XPS-13 9360 with a rickity installation of 18.04 that I haven't been able to migrate off of. I have been (for two months!) trying to copy my home folder onto an external flash drive, with little success. At the moment, I'm trying to find out if I even have any data anymore on the computer that I'm trying to migrate away from.
See:
[https://ubuntuforums.org/showthread.php?t=2501621&page=2](https://ubuntuforums.org/showthread.php?t=2501621&page=2)
I will respond to the parted -l advice tomorrow, probably; I'm hitting my daily wall updating the trail of tears from the attempts to copy my folder onto a flash drive. Meanwhile, can you explain to me what tool you use to reproduce output in those white boxes that I see here?

---

