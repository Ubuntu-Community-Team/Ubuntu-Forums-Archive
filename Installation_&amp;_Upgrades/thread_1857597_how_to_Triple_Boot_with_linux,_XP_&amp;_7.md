---
title: "how to Triple Boot with linux, XP &amp; 7"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by bheemamahesh on 2011-10-10
At present i have dualboot with XP & 7(first Xp installed & then 7)

now i want to install linux without disturbing xp & 7

i dont want to install linux by using vmware, wubi, etc...

Please Help me...

ThanX in Advance :)

---

### Post by oldfred on 2011-10-10
Not a lot different than a dual boot. Windows only boots from one active (boot flag) partition and that partition must be a primary partition. 

What is your current partition layout? You need one available primary partition to be the extended partition or have an extended partition. Ubuntu will boot and run just fine from logical partitions inside the extended partition. 

From Ubuntu liveCD post this or a screen shot from Winodws partitioner or gparted. Do use Window 7 only to shrink Windows 7 partition if that is the one you want to shrink. Use gparted to shrink XP and create any new partitions. You do not want Windows to convert from basic to dynamic partitions.
```

sudo fdisk -lu
```
(el & you at the letters not one or eye)

---

