---
title: "Help needed with creating dual boot system"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by wizardraghnall on 2010-10-31
I am currently running Windows Vista... and I want to install Ubuntu 10.10.  Just wondered if anyone can tell me how to install Ubuntu alongside my Windows OS so that I can still play WoW and other windows games.

Thanks!

---

### Post by P4man on 2010-10-31
For the record, WoW works on ubuntu although it might be a bit tricky to get working, so a dual boot is the best idea for now.

Its really rather simple. Just create a bootable ubuntu CD and boot from it. Then you can try ubuntu from the cd, and click the install icon when you are ready to install. A wizard will guide you through the process of setting up the dual boot.

---

### Post by jroa on 2010-10-31
> **wizardraghnall said:**
> I am currently running Windows Vista... and I want to install Ubuntu 10.10.  Just wondered if anyone can tell me how to install Ubuntu alongside my Windows OS so that I can still play WoW and other windows games.

Thanks!

There are several ways to do it, but the easiest is just to run the live CD and choose to install the program.  When you are asked what partition to install on,  choose to create a new partition from the Windows partition.  I am not running the program, so I can not see exactly what the verbage is, but it is pretty self explanatory as you install.  If you are affraid of screwing up your Windows partition, you can back it up before you try it.

---

### Post by wizardraghnall on 2010-10-31
Thanks.  I am really grateful for the help.  I am nervous about screwing it up.

Where do I back up to so that I can be sure the back-up won't get deleted?

Also on my current system I have my C: drive which has my regular Windows on it.... and then I have a D: drive which has other pictures, documents etc.  I am not sure if these are too separate drives or just a partition that came with the computer.  What I need to know is how to create the partition and where to create it?  Do I need to move anything to make room?

Thanks again.:)

---

### Post by P4man on 2010-10-31
Backup to an external drive or other machine.  If you only have one drive and you really mess up, then no amount of backing up to the same drive you are about to overwrite will help.

As for you having one or two drives, you will see once you launch the installer. It will show you your drives and partition and how much space you have on them. But just booting the CD and trying out ubuntu without installing is completely safe. That would be your first step.

---

### Post by wilee-nilee on 2010-10-31
I think the key here is first we should know how many partitions are on the hard drive now. Vista should be resized with a appropriate partitioner W7 has a virtual one built in I think Vista does as well. If it doesn't gparted can be used, but with W7 you untick the round to cylinders to do so, it may be the same for Vista.

The reason for resizing Vista first is so it can be rebooted and be confirmed to be still working. Then you would just install to the unallocated free space left.

You can do customized installations as well in the free space. You will if done right have a logical partition for the linux primary and swap partitions. You can have a unlimited amount of primary type partitions inside the Logical.

I think P4man is correct with the backup, a whole HD image would be my choice, but if you have the install disc and stuff saved that you can't lose then you can proceed as you think prudent. Just make sure to have your self covered for any possible scenario. Which is a simple as a whole image on a external hard drive that you are sure reloads.

---

### Post by oldfred on 2010-10-31
Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Some examples of installs.
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

