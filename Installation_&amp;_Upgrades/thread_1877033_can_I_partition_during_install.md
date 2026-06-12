---
title: "can I partition during install"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by myengliah on 2011-11-07
Hi all,  I have vista home premium in the laptop which is having some problem and not going beyond the log in screen. After logging in all I see is just a black screen. At the moment the laptop has only one partition and my doubt is, can I install Ubuntu in the laptop and while installing can I partition the disk and put ubuntu in the new partition rather than C where Vista is reigning?  Any help is much appreciated and thanks all in advance  KL

---

### Post by coffeecat on 2011-11-07
Yes, you can. In theory you can shrink the Vista C: partition and make your Ubuntu partitions in the freed space. However, using a Linux partitioner, such as Gparted that comes with the Ubuntu live CD, can sometimes cause Vista to become unbootable. This is fairly easily fixed, but this is why it is often recommended to use Vista's Disk management to shrink the C: partition.

But, of course, you can't at the moment. If at all possible I suggest you research your Vista problem more to see whether you can get it booting again so that you can use Disk Management in Vista. If you shrink the C: partition with Gparted you may simply compound whatever has gone wrong with Vista.

About partitioning in general for Ubuntu, here's a useful link. Follow the links within it and you'll get a good overall idea of partitioning principles and how to use Gparted.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by WasMeHere on 2011-11-07
Short answer: Yes :-)

Longer answer:

0. Before you do anything to your HDD, please take your time to find out which version (time-wise) and flavour (desktop-environment-wise) of Ubuntu, that suits you! Browse the Ubuntu Forums and internet in general for advice. Many people have already done what you intend to do, and they have written about it.

1. Then make a backup of your present state of the HDD, because editing partitions is risky!

2. I suggest that you run a *live* system from an ubuntu installation disk and use *gparted* to edit your partitions.

3. After that you can install Ubuntu to your HDD.

Have fun finding out :-)
Olle

---

### Post by BillyBoa on 2011-11-07
If you don't like to make changes to your partitions, you could install Ubuntu using Wubi.exe which is included in the Ubuntu CD.

---

### Post by Mark Phelps on 2011-11-07
> **BillyBoa said:**
> If you don't like to make changes to your partitions, you could install Ubuntu using Wubi.exe which is included in the Ubuntu CD.

I believe that you have to be able to RUN MS Windows to install using wubi -- and given the OP's comments > After logging in all I see is just a black screen. 
 THAT is not possible.

To OP, if you have another PC, you can look around for Partition Wizard. That's a free MS Windows partitioning tool.  They have an option to download a CD ISO file -- which you can then burn to CD, boot from that, and use that to shrink your Windows partition safely.

---

