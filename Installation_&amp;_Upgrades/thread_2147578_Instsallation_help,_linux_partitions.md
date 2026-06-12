---
title: "Instsallation help, linux partitions"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by a1b2 on 2013-05-22
I need actual how to instruction on creating the required partitions for ubuntu to install.
I am trying a dual boot, win xp/ubuntu.
Fresh xp install (since first attempt at ubuntu 12.04.2lts wiped xp).
Winxp is on c drive, had created d drive (34GB) to install ubuntu on but no joy.
Deleted d drive in windows hoping ubuntu would install in the free space, no joy.

So now I have 34GB of free space in which I would like to install Ubuntu and all it's required partitions.
What do I do now?

---

### Post by jbeiter on 2013-05-22
It's not too difficult. Boot off of an Ubuntu disk. When you run the installation, ubuntu will present you with different partitioning instllation options (such as wipe everything out, install ubuntu, install ubuntu along side of something else, etc..)

Although I've never actually used it, it should detect that you have a windows partition and offer to install ubuntu on your 34G partition.  

If you want to create custom partitions for ubuntu (ie: dedicated, root, /boot, /home, etc...) choose "Other" when you get to those partitoning/installation options. It will give you a screen for a partition tool. It should detect your windows partition, and the other 34G one (it might think it is windows or "free")  if it is not free, just delete it and then it will be free. You can then highlight it and use the "+" buttons to specify the new partitions to create... ext4, give it a mount point. Rinse/Repeate until your space is used up, then install. It will install a boot loader and you should have both your windows and ubuntu as boot options.

---

### Post by a1b2 on 2013-05-22
Thank you for the reply.
Would not install in the reserved D drive, wanted to install in c. Finally installed in deleted d drives empty space.
Been a LONG journey.

Ubuntu is running so I guess we can close this thread.

---

