---
title: "Shuffle partitons around"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by whinis on 2011-04-30
This may not be the best location however this seemed like the best spot I could find. I already have ubuntu 11.04 installed on my computer and have the following partitions

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20481851   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2551       12278    78140160    7  HPFS/NTFS
/dev/sda3           12279       38913   213945637+   5  Extended
/dev/sda5           12279       12776     4000153+  82  Linux swap / Solaris
/dev/sda6           12777       38913   209945421   83  Linux

```where 
/dev/sda1 is a windows recovery partiton
/dev/sda2 is my windows 7 partition
and the rest is obvious.

I would like to split my linux / partition into 3 partitions being / /boot and /home so that I can encrypt / and /home as well as for possible screw up protection. in what way could I do this ?

---

### Post by Hedgehog1 on 2011-04-30
This is done by shrinking a partition, using that new space to create new ones, and then copying the data to the new partitions.

May I suggest you limit yourself to these three partitions:

'/' root,
'/home'
Swap.


The separate '/boot' partition has been causing more problems than it solves lately when it suddenly runs out of space as new kernels are added.  But it is your machine.  :D


Here is a nice guide to moving '/home' to is own partition.  It is the one I used myself, actually: **_[move-home-to-its-own-partition]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")_**


***The Hedge***

:KS

---

### Post by whinis on 2011-04-30
I am not worried about boot running out of space, I figure give it about 1gb and it should be fine for awhile ( current is at 76 mb). However it seems that I might need a little time to complete this ( /home =235 gb).

Also I recently had to fix my machine due to the natty upgrade. It completly destroyed my graphics driver, grub config, and indicators.

---

