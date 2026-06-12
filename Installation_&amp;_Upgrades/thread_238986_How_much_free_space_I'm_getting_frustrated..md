---
title: "How much free space? I'm getting frustrated."
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by xybermaster on 2006-08-18
Ok so I started up the installation wizzard. So there are three options to install ubuntu. The first one is to dual boot. It takes the free space and use it for the installation. I have 15GB free space which I allocated to ubuntu yet I get an error message saying "Not enough space created for installation." Whats up with that. I want to have windows and ubuntu on the same hd. CAN SOMEONE PLEASE PLEASE PLEASE HELP ME. I REALLY WANT TO INSTALL UBUNTU. Its the 6.06 LTS for PC version.

---

### Post by givré on 2006-08-18
15 Go should be enough.
If you can provide some screenshot to show what's happens, that's could be helpfull.
Thanks

---

### Post by meng on 2006-08-18
Yes, some details would be helpful. Is this 15GB of contiguous free space, or is your Windows drive fragged to all hell?

---

### Post by xybermaster on 2006-08-18
It is in the same partition with windows. Its one hd I have with 2 partitions. Partition 1 with 36.4GB with 10GB free space and partition 2 with 38GB with 3.45GB free space. And I cannot provide a screenshot since I am running it on the live cd.

---

### Post by christhemonkey on 2006-08-18
You do know that you have to resize these partitions and create new ones?
You cant just use old partitions straight off.

---

### Post by givré on 2006-08-18
and don't forget to defragmente before doing that. 
When it show 10 G at the end at the partition, it rarely the case, it's more 10 Go disperse into your 140 Go :cool:

---

### Post by xybermaster on 2006-08-18
Ok then please tell me what must be done to use the first option of installing ubuntu. If I cant use the first option then it makes no sence.

---

### Post by givré on 2006-08-18
Choose the manually edit your partition table option.
And create a partition for ubuntu at the end at your 130 G partition.

---

### Post by avtolle on 2006-08-18
Before installation: defrag, defrag, defrag...; then, shrink the size of the Partiition you have Windows on; then, create a new, empty partiiton on the HDD; then, run the Ubuntu disk, select the first option. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) discusses how to set up your HDD to dual boot, which is what it appears you want to do. Note that his guide assumes you are using the text based installer, not the Graphic Installer found on the Desktop CD. The Alternate Install CD (which you must download and burn as an iso image to CD) contains the text based installer. HTH, and post back with your questions.

---

### Post by jimbren on 2006-08-18
You need to defragment your drive from Windows before attempting to do the installation.  Windows writes data all over the place, but when Ubuntu (or any other distro) tries to install it will look only for contiguous free space.  If there isn't enough (because Windows has written a bit here and a bit there), it will fail.

---

### Post by xybermaster on 2006-08-18
> **jimbren said:**
> You need to defragment your drive from Windows before attempting to do the installation.  Windows writes data all over the place, but when Ubuntu (or any other distro) tries to install it will look only for contiguous free space.  If there isn't enough (because Windows has written a bit here and a bit there), it will fail.

Ok I'll try the above and if it don't work i'll be back later. Thank you for your support.:p

---

### Post by jimbren on 2006-08-19
Did that work?

---

