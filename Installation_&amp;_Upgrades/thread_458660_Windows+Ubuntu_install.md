---
title: "Windows+Ubuntu install"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by madmagic on 2007-05-29
ok i recently repartitioned my disks so i can have the option of running both Windows Xp Home, and Ubuntu... but the install seems to want to do the whole disk, i tried Manuel  but all i get is No Root System Defined.. help please?

Madmagic

---

### Post by RevNL on 2007-05-29
Did you set the label of your Linux partition as "/"?

---

### Post by madmagic on 2007-05-29
thank you for your help, i can continue with a new error, but i want to try it at its peek

You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory.

If you do not go back to the partitioning menu and assign a swap partition, the installation will continue without swap space.

is my error

---

### Post by RevNL on 2007-05-29
Sounds like you have a root partition now.  Good.

How did you partition the drive?  Did you create a swap partition?  If not, delete your new Linux partition and create a new smaller one (labeled as "/") and use the leftover space to create a swap partition.  It should be equal to or larger than the amount of RAM.

---

