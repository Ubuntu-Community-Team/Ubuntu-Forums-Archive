---
title: "problem to reinstall Ubuntu 10.04"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by ganjaboy on 2010-07-28
HI ,
I'm still having problem to reinstall my Ubuntu. This time i plan to move towards 10.04 and I am not sure how to uninstall my existing 9.10. I did partition and running both XP and Ubuntu. Each time, i restart my PC, I tried to boot from new disk 10.04 but only managed to install the live CD and the old 9.10 is still there. I need to remove the 9.10 completely and install a fresh Ubuntu 10.04. I have some data on 0.10 and am i would be able to retrieve that?
Could some one provide me the steps to remove my existing Ubuntu and install back the new one on the same partition. I'm a beginner and would need a quite detail steps so that i can perform the installation successfully.

Thanks in advance guys.

Regards,
MK

---

### Post by Revolutionary101 on 2010-07-28
You don't have to do a fresh install, it can be a lot easier to upgrade to Ubuntu 10.04 via the repositories or the CD that you have (To do this just pop the CD in and your computer should detect Ubuntu 10.04 and ask you if you want to upgrade). This way you won't have to worry about the hassle of deleting partitions.

Before you do anything for the fresh install, copy your the files that you need to an external hard drive or flash drive. Once you finish the install you will be able to copy them back to your computer.

To do the fresh install, I would suggest running off of your Ubuntu 10.04 LiveCD and go to System>Administration>GParted. From there you can see all of the partitions on your HDD. Find the partitions that have the file systems ext4 and extended (you should also have a ntfs partition but don't touch that. Windows XP is on that partition). Then delete those (after you have backed up your data of course). Once you run the installation you should be able to select the "Largest continuous space" to install Ubuntu on.

---

