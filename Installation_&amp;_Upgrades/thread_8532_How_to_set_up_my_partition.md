---
title: "How to set up my partition?"
date: 2004-12-18
forum: Installation &amp; Upgrades
---

### Post by Dko on 2004-12-18
Well I just got my disk and tried installing Ubuntu.  Beffore had I used f-disk to create on my second hard drive two partitons.    But In the instalation I get to a point where it asks me to format one or the other of my hard drives or to manualy edit my partitions.  My question is how would I have to manualy edit the partition im using to get it to work with the install?

---

### Post by Rancoras on 2004-12-18
If you select the manual edit option, the menus are fairly self-explanatory.  Basically you need a minimum of 2 partitions.  One for your system, and one for your swap.  I usually make the swap 1.5 times the system memory, up to a max of 1 GB.  You can pick whatever filesystem you want for your main partition, if your unsure, just use ext3.

As always, if you are planning on dual booting with windows, make sure you back up any data you can't afford to lose.

---

