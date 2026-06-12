---
title: "Creating 4KB aligned partitions during 10.04 install"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by aaime on 2010-05-01
Hi,
I'm currently running a Ubuntu 9.10 64bit machine with one of those 2TB WD disks that does have 4KB blocks.

Unfortunately the current partition layout is misaligned, so I plan to back up my home directory and start fresh with a 10.04 install, trying to make the partitions aligned as suggested here:

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)

Now, what I'm wondering is, does the 10.04 partitioning program take care of the alignment today or I have to resort doing manual partitioning with a separate tool?
Does anyone have a guide?

---

### Post by Herman on 2010-05-01
The Ubuntu installer's partitioning program does not yet (as far as I am aware), have the ability to create partitions other than on the traditional cylinder boundaries. However, if your partitions have already been created prior to you starting the Ubuntu installer, the Ubuntu installer will install in them without moving them at all.

You only need to create your partitions as described in the web page you linked to, either with fdisk or with GParted.

Then run the Ubuntu installer and designate the partition(s) you made for formatting with whatever file system(s) you like and specify how you want each one mounted, (as /, /home, /boot and so on ... ).

The Ubuntu installer will respect the location(s) of the partition(s) you created and leave them where they are.

---

