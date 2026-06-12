---
title: "Dual Booting WindowsXP and Ubuntu. 1 HDD"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by Jordan777 on 2007-06-22
Hi!  I have a very frustrating problem.  I already installed XP and I gave it a little less than half of my hard drive space (total memory=320GB) and I am just stuck on the partitioning of Ubuntu.  I Know I need a Ext3 / partition of about 6~10GB and I need a Swap partition of 3GB or so.  Now I'm torn here.  I want to make both a /home and a fat32 partition.  I want to make my fat32 partition 10~15GB just in case I need to share documents.  Then I will give the /home the rest of the memory.  What I'm trying to accomplish here is make Ubuntu my main OS and still have some games on it while my Windows OS is mainly ONLY games and a few documents.  My questions are does my proposed partitioning setup sound ok?  Also do I need to make extended drives out of the stuff for Ubuntu?  I'm not sure how many partitions I can have on 1 hard drive.  Last but certainly not least is GRUB pre-loaded on the Ununtu 7.04 LiveCD installation?  If not I need to know how to install it so that I may choose from which operating system to boot from when I start up.  I really need to know because right now the only thing running my comp is a LiveCD as I have to talk to MS about a product registration key :(.  ANY and ALL help is very very very much appreciated.  I will be hanging around this topic till around 10:00~10:30ish so please don't be afraid to help.  Also sorry for my wall of text ;) newbies ya know?

---

### Post by NeoLithium on 2007-06-22
Welcome to Ubuntu!
Well, I'm not a dual boot guru, you can actually shrink that swap space unless you have a need for crazy memory, the old days of 2x your RAM are pretty much gone, I have mine equal to my ram (512MB) and things run smoothly and barely touch the swap. It just sepends on your tasks that you plan on doing, really.  Hard Drives can have 4 primary partitions on them, so you should be fine with the /, /home, swap and storage partition. As well, grub will be installed with Ubuntu from the liveCD.

---

### Post by Jordan777 on 2007-06-22
That's what I thought I saw about the 4 main partitions thing with the hard drive.  Thank you for that information also about GRUB thank you again.  Now my main problem is I would have 5 main partitions.  The NTFS of Windows, the /, Swap, /home, and Fat32.  Anybody know what to do here?  Oh and the Swap=3GB because my ram is 2GB :KS.  I thought I'd just do 1.5x my ram.  But maybe I'll just do 1x.  So anyone know what to do about my partitioning situation?  Again, this is only on one hard drive. :D

---

### Post by Jordan777 on 2007-06-22
OK actually I'm in the clear.  I just installed without the Fat32 partition which I can add later.  Thank you for your help!!

---

