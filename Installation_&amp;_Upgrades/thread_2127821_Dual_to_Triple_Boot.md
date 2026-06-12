---
title: "Dual to Triple Boot"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by excollier on 2013-03-21
Here is a screenshot of my laptop hdd.
Is it possible to simply add a third os to this laptop?
Ubuntu 12.04, #! and Linux Lite are strong contenders.
I was thinking of letting Ubuntu simply fit into sda5 alongside Linux Mint, as I store all my data in sda3 at the moment, so all I need is space to fit the o/s.
Would Ubuntu make the decision for me and slot in elsewhere, (sda2 or 3 maybe) and set grub to boot all 3 o/s?
I had no trouble setting up the dual boot, and it is very important to keep Windows Vista working because my wife uses Office 2010 on that.
The laptop is an Acer Aspire 5535 with AMD Turion X2 Dual core 64 processor and 4GB Ram

---

### Post by Mark Phelps on 2013-03-22
> **excollier said:**
> ... and it is very important to keep Windows Vista working because my wife uses Office 2010 on that.

Understand your concerns, so I have two comments ...

First, you should download and install the free version of Macrium Reflect in Vista, use the option to do an image backup of Vista to an external drive, and use the option to create and burn a Linux Boot CD.  With these, you have the means to completely restore Vista in a few minutes -- should anything go wrong during your multi-boot setup.

Second, if you need more disk space for your next OS, then use ONLY the Vista Disk Management utility to shrink Vista.  Do not use GParted or the Linix distro installer to do this -- as that has sometimes resulted in corruption of the Windows filesystem, rendering it unbootable.  After you do the shrinkage, boot back into Vista a couple of times so it can do any needed filesystem adjustments.

For safe keeping, after you do the shrinkage, you should run another MR backup.  This will allow you to restore the "shrunked" version of Vista, should you need to.

---

### Post by grahammechanical on 2013-03-22
> [COLOR=#000000]I was thinking of letting Ubuntu simply fit into sda5 alongside Linux Mint,[/COLOR]

Do not try that. I do not think that it will work. You will have to create space for another partition of about 10GB inside the Extended partition (sda4). You will not need another swap partition. Ubuntu will use the existing swap partition (sda6).

Take the advice given by Mark Phelps and also study partitioning in Ubuntu and installing Ubuntu using the Do something Else option.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Image 7 in this link will show you what you see when you choose the Do Something Else Option and get to the partitioning section.

[http://news.softpedia.com/news/Installing-Ubuntu-12-10-301012.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-10-301012.shtml)

Select the partition that you newly created just for Ubuntu and press Change. At the little menu that appears select a file system - Ext4;  select a mount point - /; mark for format and accept these changes. That will take you back to the partitioning screen where you will see the changes marked in the layout. Now continue with the install.

Regards.

---

### Post by matt_symes on 2013-03-22
Hi

> You will not need another swap partition. Ubuntu will use the existing swap partition (sda6).

This will not be a problem as long as you do not hibernate your Linux installs. If you do, create a separate swap partition for each Linux install as the hibernation image is kept in the swap partition in a default install.

If you never hibernate then this advice is great.

Kind regards

---

### Post by excollier on 2013-03-22
I've decided to be happy with what I have, rather than risking a lost Windows install for the sake of experimentation.
Thanks for your thoughts and helpful advice. Since I started tinkering with Linux a few months ago, I have learned a lot from contributors such as yourselves. A real, free and enjoyable education.

---

