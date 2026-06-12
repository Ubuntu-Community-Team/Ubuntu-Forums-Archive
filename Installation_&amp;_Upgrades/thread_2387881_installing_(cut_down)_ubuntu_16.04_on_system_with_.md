---
title: "installing (cut down) ubuntu 16.04 on system with very small SSD"
date: 2018-03-25
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2018-03-25
I have an installation of Ubuntu 16.04 on a system (an odroid x2) with a very small SSD (less than 10 GB, an eMMC). The drive is nearly full.  I have a spare 16 GB on an attached SDHC.  How do I move some system folders to the SDHC to stop the eMMC getting full? Which should I move (the eMMC performs a lot better than the SDHC in terms of speed). Any guides on this?
Thanks very much for any help.

---

### Post by Impavidus on 2018-03-25
How much do you want to move away from the SSD? The basic system should fit (just) in 10GB, provided you don't install too many applications. Then you can move /home (which has your documents) to the other drive. If that's not enough, /var and /usr are candidates to move, but that will hurt performance. It's probably best to move things while running a live session, but /home can be moved while running the installed system.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Hodor on 2018-03-25
Thanks Impavidus. I've noticed since posting this that the SSD should actually be larger, so I'll trying fixing that then hopefully moving the home directory will be all I need to do. Kind regards

---

### Post by mörgæs on 2018-03-25
When you some day install 18.04 there will be an option to select a minimal system during the installation. You can also consider Xubuntu Core. 

Moving /home is still a good idea, also when using the methods mentioned here.

---

### Post by Hodor on 2018-03-26
Thanks morgaes - all fixed now, just had to enlarge the partition.

---

### Post by mörgæs on 2018-03-27
Good, please mark the thread solved.

---

