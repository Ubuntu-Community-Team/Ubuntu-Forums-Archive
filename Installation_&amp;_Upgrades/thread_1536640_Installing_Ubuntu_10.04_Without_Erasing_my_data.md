---
title: "Installing Ubuntu 10.04 Without Erasing my data?"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by darkmech on 2010-07-22
I Already have windows 7 installed on my computer , when installing ubuntu if I chose the option "Install them side by side, choosing between them at each startup." will all my files and data stay the same. i'm afaird to install it unless i know i wont lose anything.

---

### Post by gdonwallace on 2010-07-22
Installing Ubuntu "beside" windows is essentially the wubi installer taking a chunk of your hard drive and creating a partition to install Ubuntu on.  In this way, Windows files are not touched by Ubuntu and the other way.

The only real downside would be if you needed access to those windows files.  It takes a little work, but it can be done.  No, if you do this, Your windows files will be fine.

---

### Post by QIII on 2010-07-22
Use the partitioning tools in Windows to shrink your Windows partition after defragging a couple of times.  Let Windows decide whether or not and where the shrinking can take place. 

After you have made space, install as a dual boot, but be very careful to not overwrite your Windows partition.

In a genuine dual-boot system, you can access the Windows partition without much trouble at all, although you can't run the Windows OS or any of its programs.

But, as always, when you are about to do something significant to your machine BACK UP IMPORTANT FILES!  BACK UP IMPORTANT FILES!  BACK UP IMPORTANT FILES!  In this case, since you stand the risk of overwriting your fixed media, back up to removable or remote media.


> **gdonwallace said:**
> Installing Ubuntu "beside" windows is  essentially the wubi installer taking a chunk of your hard drive and  creating a partition to install Ubuntu on.

No, the Wubi installer would have nothing to do with it.

Wubi installs Ubuntu inside Windows, generating a Windows folder inside  which Ubuntu happily believes it has a real partition.  A Wubi install  can be uninstalled just like any other windows program.

A side by side installs the operating systems natively on their own  partitions on the hard-drive, totally independent of each other.

---

### Post by techunit on 2010-07-22
> **gdonwallace said:**
> Installing Ubuntu "beside" windows is essentially the wubi installer taking a chunk of your hard drive and creating a partition to install Ubuntu on.  In this way, Windows files are not touched by Ubuntu and the other way.

The only real downside would be if you needed access to those windows files.  It takes a little work, but it can be done.  No, if you do this, Your windows files will be fine.
Please don't pay this message any merit as it is irrelevant to your situation...

---

### Post by techunit on 2010-07-22
> **techunit said:**
> Please don't pay this message any merit as it is irrelevant to your situation...
Please please please don't install Ubuntu beside windows using the Ubuntu Live CD as it will break your windows installation and you will have to fix it. While if you do break it your in luck by the fact that it is easy to fix provided that you already have a Windows Install/Restore Disk. What you will have to do is shrink your windows partition using the windows disk manager (you may have more luck with Partition Wizard Home) then you can install ubuntu to the free space you have created for it.

---

### Post by darkmech on 2010-07-24
> **techunit said:**
> Please please please don't install Ubuntu beside windows using the Ubuntu Live CD as it will break your windows installation and you will have to fix it. While if you do break it your in luck by the fact that it is easy to fix provided that you already have a Windows Install/Restore Disk. What you will have to do is shrink your windows partition using the windows disk manager (you may have more luck with Partition Wizard Home) then you can install ubuntu to the free space you have created for it.

yea i have a external harddrive with 2 seperate partitions, if i install it on a partition thats empty the installation shouldnt even effect any other drives , right.

---

