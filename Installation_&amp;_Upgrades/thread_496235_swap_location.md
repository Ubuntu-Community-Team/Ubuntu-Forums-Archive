---
title: "swap location"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by coca.cola.armageddon on 2007-07-08
When I allow the installer to partition my disk during installation, it always puts the swap on an extended partition, like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4723    37937466   83  Linux
/dev/hda2            4724        4864     1132582+   5  Extended
/dev/hda5            4724        4864     1132551   82  Linux swap / Solaris

Why does it do this?  Why doesn't it make hda2 a primary partition and put swap on it?

If I manually create two primary partitions (hda1 as root, hda2 as swap), would I be jeopardizing the system?  Thanks for any input.

-Tom

---

### Post by Pumalite on 2007-07-08
What's the object of your proposal?

---

### Post by coca.cola.armageddon on 2007-07-09
The amount of swap the installer allocates is based on the amount of ram currently installed, but I want to allocated some extra swap, as I might want to install more ram in the future.  I figure I might was well allocate a lot of space now, rather than having to repartition and reinstall when I do the ram upgrade.

I was having trouble using the GUI for the partitioning tool  (This is the kubuntu 6.06 installer, by the way).  It was hard to get partitions set up in the same way they are when I let the installer auto-partition.  I was considering manually partitioning as I described in my post (hda1 as root, hda2 as swap).  I ended up not doing that, and instead I used fdisk to partition in the "proper" way, with swap space on hd5.
Although I have solved my problem, I'm still curious as to why the installer chooses to put swap on hd5.

-Tom

---

### Post by r0ck80y on 2007-07-09
If you notice hda2 and hda5 are the same. hda2 is an extended partition within which you can create more partitions called logical partitions. Right now your hard disk has has one logical partition (hda5) which occupies all of hda2. A hard disk must have an extended partition (which is also a primary partition).
 So you can delete hda2 using fdisk, create a new primary partition (of type swap) but its cylinder will start at 4724 but should be less than 4864. The remaining cylinders can be made an extended partition. Then your hdd will have 3 primary partitions (linux, swap and extended). But this doesn't solve the problem of you allocating more space for swap. You'll need to repartition the entire hard disk...reduce the size of the linux partition. Use a live CD to do this. I hope i have understood you right :)

---

