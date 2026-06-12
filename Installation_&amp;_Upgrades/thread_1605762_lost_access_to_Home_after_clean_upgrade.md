---
title: "lost access to Home after clean upgrade"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by qwedsa on 2010-10-25
Hello every one,

I used to use Ubuntu 9.10 for a year. I had my home path on different partition (19Gb) than the system partition (12Gb). Before I upgraded, the free space on Home partition (19Gb) was  6.3Gb. I knew that the direct upgrade is not good, so, I format the system partition (12Gb). Then, I install clean version of Ubuntu 10.04 on it. every thing is great. except that, I can not find my files in the old home path. In same time, Ubuntu is telling me that the Home partition (19Gb) (which I have not touch at all) has free space of 6.3Gb and used space of 11.3Gb. It means it can recognize that there is something but it can not open it at all. 


system information:
Ubuntu 10.04 (lucid)
Gnome 2.30.2
2.6.32-25-generic

Thank you

---

### Post by dabl on 2010-10-25
You installed the complete filesystem to the 12GB partition.  You were supposed to choose the partition where your data are, and mount it to /home, during the installation process.

Unless you wish to install again, and catch the other partition on /home, you'll have to (as root) delete the present /home directory, then edit /etc/fstab and mount the other partition on /home, and reboot or execute ```
sudo mount -a
``` afterward.

---

