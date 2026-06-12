---
title: "Dualbooting Ubuntu and Backtrack 5 Questions"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by daniel1455 on 2011-11-14
Okay, so heres the deal. Ive messed around with this before but dont wanna get into it without knowledge again. I have ubuntu 10.10 and backtrack 5 dualbooting together. Lets say that I eventually get sick of backtrack and want to solely run Ubuntu. How would I delete backtrack 5 along with its bootloader so that once I turn on my computer it will go straight to Ubuntu as if it were running alone. Get me? My questions pertain to removing the bootloader if I were to uninstall Backtrack 5.

---

### Post by oldfred on 2011-11-15
Welcome to the forums.

If you installed Backtrack last, then you need to first install Ubuntu boot loader to the MBR. Boot into Ubuntu and run this.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Then you can use the Backtrack partition for what ever you want. I generally suggest smaller system partitions for Ubuntu of 10-20GB. I have a larger drive and use 25GB for each of my several Ubuntu installs. You can install another system or convert to a data partition.

---

### Post by daniel1455 on 2011-11-15
Okay but what I had done was that I installed Backtrack 5 first and then installed ubuntu. The reason being was that the Backtrack 5 bootloader was giving me problems. So If I decide to uninstall Backtrack in these circumstances and remain with Ubuntu, would your steps generally be the same?

---

### Post by oldfred on 2011-11-15
If you installed Ubuntu last, its boot loader should be in the MBR, unless during the install you told it to install somewhere else?
When you boot which system is first in the menu. That is the system in the MBR that is booting.

---

### Post by daniel1455 on 2011-11-17
Ubuntu is the first item on the bootloader

---

### Post by oldfred on 2011-11-17
Then you should just have to delete the backtrack partition or reformat and use it for data. A sudo update-grub after deletion will then remove the backtrack item from the grub2 menu.

---

