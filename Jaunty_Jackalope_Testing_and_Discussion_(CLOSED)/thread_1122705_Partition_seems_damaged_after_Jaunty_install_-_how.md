---
title: "Partition seems damaged after Jaunty install - how can I fix this?"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tubegeek on 2009-04-11
Here is the result of fdisk -l concerning the problematic partition:


[FONT="Courier New"]Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43281245

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         127     1020096   83  Linux
/dev/sdc2             128       14650   116655997+   5  Extended
/dev/sdc5             128       14650   116655966   83  Linux[/FONT]


It seems I have two partitions with the same begin/end blocks - that looks wrong to me, but what do I know?

I don't know much about fixing partitions: can anybody help me walk through it? 

I have, *of course,* un-backed-up data on the sdc5 partition which I currently can't get into. I am also unable to mount that filesystem booting from a previous Ubuntu 8.10 installation. The Jaunty install hiccuped during the partitioning phase of the install, I think that may be where I got screwed up but I'm not sure.

---

### Post by tom56 on 2009-04-11
> **tubegeek said:**
> Here is the result of fdisk -l concerning the problematic partition:


[FONT="Courier New"]Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43281245

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         127     1020096   83  Linux
/dev/sdc2             128       14650   116655997+   5  Extended
/dev/sdc5             128       14650   116655966   83  Linux[/FONT]


It seems I have two partitions with the same begin/end blocks - that looks wrong to me, but what do I know?

I don't know much about fixing partitions: can anybody help me walk through it? 

I have, *of course,* un-backed-up data on the sdc5 partition which I currently can't get into. I am also unable to mount that filesystem booting from a previous Ubuntu 8.10 installation. The Jaunty install hiccuped during the partitioning phase of the install, I think that may be where I got screwed up but I'm not sure.

That's not a problem. One partition is within the other. What might be an issue is that you don't seem to have a swap partition. Try using gparted to look instead, it tends to be clearer.

---

### Post by tubegeek on 2009-04-11
I tried gparted, it was unable to recognize the sdc5 partition. It saw that it was there but was unable to work with it.

Also, to be clear, this is NOT the active boot partition, that's on a another drive.

---

### Post by taavikko on 2009-04-11
> **tubegeek said:**
> Here is the result of fdisk -l concerning the problematic partition:


[FONT="Courier New"]Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43281245

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         127     1020096   83  Linux
/dev/sdc2             128       14650   116655997+   5  Extended
/dev/sdc5             128       14650   116655966   83  Linux[/FONT]


It seems I have two partitions with the same begin/end blocks - that looks wrong to me, but what do I know?

I .

There's no problem, sdc2 is an extended partition and in that extended partition you have the sdc5 partition. It's all good, no worries.

Swap isn't essential, you can survive without it, but on low memory system you may experience unwanted behaviour.

---

### Post by tubegeek on 2009-04-11
Here's what gparted looks like.

---

