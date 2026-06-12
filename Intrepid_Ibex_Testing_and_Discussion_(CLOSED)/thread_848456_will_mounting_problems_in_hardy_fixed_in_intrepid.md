---
title: "will mounting problems in hardy fixed in intrepid"
date: 2008-07-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ajmal_82 on 2008-07-03
[FONT="Georgia"]Hate to say but iam finding hard to fix mounting partitions on _**local hdd**_,the partitions are **fat32** not ntfs because i 
already know about troubles using ntfs partitions,and are not detected by  default unlike previous editions gutsy,fawn.
Hardy didnt add entries to fstab on both occasions when i installed on my pc and friends pc,i fixed it manually still i cant see the drive labels that i gave it in xp[/FONT]:confused:
       :)hope to see change in ibex at least,also *weird* it **shows partitions as external drives** for local drives after editing fstab.

---

### Post by Nullack on 2008-07-03
Put them in /mnt not /media

Use ntfs3g for NTFS - NTFS is far better than the deprecated fat32

---

