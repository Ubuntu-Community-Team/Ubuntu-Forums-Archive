---
title: "Hard drive problem"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by satimis on 2006-08-05
Hi folks,

The HD was in problem and I ran

# dd if=/dev/zero of=/dev/hda bs=512 count=1

to correct it.  Now it becomes

# fdisk -l```

Disk /dev/hda: 40.0 GB, 4002702954 bytes
16 heads, 63 sectors/track. 77557 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          98      499360+  83  Linux
/dev/hda2              14         778     39039336  8e  Linux LVM
```

I can't create LV on it.

(remark: I'm now installing Ubuntu-6.06-amd64)


I compared it with another HD of similar brand and model in another PC

# fdisk -l```


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14         778     6144862+  83  Linux
/dev/hda3             779        2053    10241437+  83  Linux
/dev/hda4            2054        4865    22587390    5  Extended
/dev/hda5            2054        2118      522081   82  Linux swap / Solaris
```


Please advise how to reset it, making
255 heads (now 16)
4865 cylinder (now 77557)
cylinders of 16065 (now 1008)

TIA

B.R.
satimis

---

### Post by Ocxic on 2006-08-05
if you're absolutly sure about the setting i believe fdisk can change that. you cylinder/head setting will be on the label of your HD

---

