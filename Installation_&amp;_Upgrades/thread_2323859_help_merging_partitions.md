---
title: "help merging partitions"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by nickjhs on 2016-05-09
Hi all, I am trying to free up some space to install kodibuntu as a third boot option. I have shrunk two partitions and turned the freed space into  sda12 and sda 13. What I need to do now  is merge sda12 and sda13  into a single partition. Thanks for your help. 

[ATTACH=CONFIG]268943[/ATTACH]

---

### Post by grahammechanical on 2016-05-09
You should not have created those partitions. You should have left the space as unallocated space then you could have moved partitions 6 to 10 to the left so that the unallocated space was behind each partition and when it was finally behind sda 10 all the unallocated space would have been merged together. And then you create a partition out of it.

Regards

---

### Post by nickjhs on 2016-05-09
So I presume I can delete those partitons? I still dont get how to move the partitions 6-10 . sorry if I am being a bit dense.

---

### Post by yancek on 2016-05-09
In order to merge partitions, they need to be contiguous which yours are not.  Since you didn't use the option mentioned in post 2 you could use either sda12 or sda13  to install Kodibuntu.  You could then use the other partition for /home or a data partition.

---

