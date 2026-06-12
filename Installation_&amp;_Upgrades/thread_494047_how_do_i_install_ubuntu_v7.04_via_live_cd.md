---
title: "how do i install ubuntu v7.04 via live cd??"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by samee on 2007-07-06
i have just received the Ubuntu live cd version 7.04 via the post and booted it up and thought it was good there fore i need help installing it on my HDD. i have partitioned the HDD into three segments, one for windows vista approx 20gb, one partition for files and data approx 40gb, and another for Ubuntu approx 20gb.

after creating the partition in vista and booting form the live cd of Ubuntu i clicked install and followed the on screen instructions i then highlighted the partition where i wanted to install Ubuntu to but is said something about swap and setup would not continue. 

what might be the problem??

---

### Post by mysticrider92 on 2007-07-06
I think Ubuntu needs an extra swap partition to install. Since you are comfortable enough using Vista's partitioner, I would add one small fat32 partition on the drive. Most people recommend a 1:1 ratio between swap and ram, but it is fine to just do 512mb or maybe 1gb. Then boot the Ubuntu cd and use the manual partitioner to format the 20gb Ubuntu partition as Ext3 and the small fat32 partition as Linux Swap. Just be careful not to touch your Vista partitions, that can destroy all data on them.

---

### Post by samee on 2007-07-06
so is this what i have to do just to clarify:

1) make a 512mb-2gb partition using vista's partition manager.
2) reboot the computer with the Ubuntu cd in side.
3) by using the manual partitioner to format the 20gb partition already made to an Ext3 and the 512mb-2gb partition to Linux Swap

and what would i do next??

and please correct me if wrong. thanks

---

