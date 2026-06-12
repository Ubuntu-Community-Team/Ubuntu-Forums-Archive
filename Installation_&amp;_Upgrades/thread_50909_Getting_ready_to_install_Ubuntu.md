---
title: "Getting ready to install Ubuntu"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by dclaridge on 2005-07-21
Hi,

I've just downloaded the Ubuntu (Hoary Hedgehog) x86 ISO and installed a brand-spakin-new Seagate 120GB HDD as the Slave on my primary IDE controller. An 80GB Seagate is currently the master drive and has Windows XP Home SP2 installed.

Before I proceed with the installation I would like to clear a few things up that the Community Documentation on the Wiki didn't quite seem to explain very thoroughly.

My first question is with regards to partitioning - I would like to create separate partitions for /, /home, /boot, and /swap on my new drive, without touching any of the partitions on the other drive. After a bit of reading it seems to me that some users have had a little difficulty in using the partition utility in the install, would somebody be able to walk me throgh exactly what I would have to do to set this up?

Secondly, when installation gets to the part about installing a bootloader, what exactly should I do? I want a selection screen to appear when the system boots, with Windows XP being the default option (to make it easier for the other users of the computer who will not be using Linux). I have read that some people have had trouble with Windows overwriting the MBR the next time windows is loaded, stopping the GRUB selection screen from appearing. How do I avoid this issue?

Many thanks in advance - looks like a great distro, and I can't wait to start using it... I'd just rather be safe than sorry.

Dave :-)

---

### Post by jasmuz on 2005-07-21
Well hello there..

First, when partitioning Ubuntu, makes a separate partition for / and another for swap, if you wish to do differently...when it comes to the partitioning phase, just do a custom partitioning scheme. remember to set the mount points for each partition and make the swap partition the double of your Ram value.

Regarding the instalation of the bootloader, it will ask you wich disk you wish to install it to, make sure you install it to the same drive you are setting the system to, and it will automagicly add the WinXP system to its list,.

---

### Post by dclaridge on 2005-07-21
Yes I realise thats what I need to do, what I'm asking is actually 'how' to use the partition tool on the install CD, as I have heard that some people have difficulty with it.

With the bootloader - what do you mean by 'make sure you install it to the same drive you are setting the system to' setting the system to?? Do you mean the drive I am installing Ubuntu to, or the drive with Windows XP?

---

### Post by irusun on 2005-07-22
Unfortunately, I don't have exactly the answers you're looking for, but...

I think most people having "problems" with partitioning are those trying to re-partition an existing drive that already has Windows on it.  Since you have a brand new empty drive, installing Ubuntu on it is a no brainer.  I don't have exact steps (I've been doing this long enough that I don't really pay attention to such things), but just make sure when you get to the partitioning/installation that you create the partitions on your *new* drive and then select /, /home, etc. respectively for each partition.  Sorry I can't be more specific than that, but I think you should just go ahead and try it - if you get to that stage in the installation and don't know what to do, cancel and come back to the forum, and ask a *specific* question about what/why you don't know how to do.

Regarding the grub bootloader, others may do it differently, but on my multi-drive setup, I've installed grub in the mbr of my first hard drive (that terminology is slightly off, but let's keep things simple).  Don't install grub to a different partition.  Ubuntu automagically added Windows to my grub list. You should look up on the forums how to add Windows to your grub list and how to set it to default (you're not the first) and print that out for reference just in case you end up needing it.

Best of luck.

---

### Post by dclaridge on 2005-07-22
So I install grub to the hard disk Windows is currently installed on? This will not affect my windows installation?

---

### Post by uniko on 2005-07-22
[QUOTE=dclaridge]So I install grub to the hard disk Windows is currently installed on? This will not affect my windows installation?[/QUOTE]

No, unless it goes awry. Although you'll lose GRUB if you decide to reinstall Windows or do fixmbr on windows, which will replace Grub with ntloader.

---

