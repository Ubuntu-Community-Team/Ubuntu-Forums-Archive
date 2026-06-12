---
title: "Can't install due to HDD partition issues"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by shawnblanchette on 2015-01-14
The pictures will say it all. I am trying to install Ubuntu (Kubuntu) on an HP G60 laptop. I have ran Check Disk, disk defrag, used Crystal Disk Info (under Vista), and AVG PC Tune Up, and other scans. No Linux installers (including Parted magic) can find the partitions properly. I am at a loss how to explain it. Hopefulle the pics will surfice.

---

### Post by oldfred on 2015-01-14
From live installer's terminal post these:

sudo parted -l
sudo fdisk -lu

---

### Post by fantab on 2015-01-14
Do you have another OS installed? Is it hibernating? If it is then disable Hibernation.
Post the output of the above requested commands, after you've boot the Ubuntu DVD/USB in 'Try Ubuntu' mode.

---

