---
title: "Installing onto USB drive"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Jsommers01 on 2011-04-21
Hello,

I am trying to install 10.10 onto my external hard-drive. I have begun the installation process and have gotten to the spot where it asks me if I want to format my computer or install along side it, how do I make sure that it is going to just be installed on my external drive? I had looked at the official instructions but they didn't mention this situation. 

Any assistance would be appreciated.

---

### Post by KegHead on 2011-04-21
Hi!

A little more info please!

---

### Post by Jsommers01 on 2011-04-21
What additional information would you like. The HDD I am installing it onto is 400GB, if it makes any difference the drive in question is actually an internal drive that a friend of mine took out of his computer and put inside an enclosure. the computer I am using is a HP with 6GB of RAM and a 64bit AMD processor (unsure of processor speed). here is a screen shot of what screen I am currently on.

[http://img849.imageshack.us/i/screenshothb.png/](http://img849.imageshack.us/i/screenshothb.png/)

If it makes any difference I am installing it off of a CD.

---

### Post by oldfred on 2011-04-21
You really want to use manual install and create partitions either as part of the install or before hand. The default installs put the grub2 bootloader to sda which is usually your internal drive. The only way to get the combo box that asks which drive to install the boot loader into is to use manual install.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I like smaller system partitions 10-20GB and larger data partitions. Then the files most used as part of the system are closer on the drive.

with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by collisionystm on 2011-04-21
> **Jsommers01 said:**
> Hello,

I am trying to install 10.10 onto my external hard-drive. I have begun the installation process and have gotten to the spot where it asks me if I want to format my computer or install along side it, how do I make sure that it is going to just be installed on my external drive? I had looked at the official instructions but they didn't mention this situation. 

Any assistance would be appreciated.



Simple.

Unplug your other hard drives before you start the install. That way you know you cant screw up.

---

### Post by C.S.Cameron on 2011-04-21
collisionystm is right, disabling the internal drive is safest and makes for the cleanest grub.
If this is too difficult or voids warranty, when you get to partitioning use manual and confirm "Device for boot loader installation" points to the USB drive. (Default should be ok if HDD was unplugged).

---

