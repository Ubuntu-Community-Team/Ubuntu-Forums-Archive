---
title: "cannot create more partitions / unusable space (having only 3 primary partitions)"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by vjpotter on 2011-07-25
I am trying to install Ubuntu on my hard disk which already has Windows 7 installed in it.
My hdd is partitioned currently as follows:
150gb - NTFS - Primary - Windows 7
60gb - NTFS - Extended (Logical) - Additional drive for data in windows
100gb - Free space

Now I am trying to create three partitions in this 100gb free space: root, swap, home.
I assigned 25gb for root and put it as another primary partition.
When I create the second partition (doesn't matter whether it is home or swap) it does not ask me for primary or logical type.
However, the remaining space left in the disk for the third partition (swap or home) becomes unusable.

What is the problem here as I am sure there are not more than 4 primary partitions already?

---

### Post by Quackers on 2011-07-25
Welcome to UF.
Presumable the 100GB free space is outside the extended partition, if you can create one primary partition in it.
As you have Windows 7 I would imagine that there is also a 100MB to 200MB in size primary partition called System Reserved. Is that so?
That would explain your problem - 4 primary partitions being the maximum.

---

### Post by vjpotter on 2011-07-25
> **Quackers said:**
> Welcome to UF.
Presumable the 100GB free space is outside the extended partition, if you can create one primary partition in it.
As you have Windows 7 I would imagine that there is also a 100MB to 200MB in size primary partition called System Reserved. Is that so?
That would explain your problem - 4 primary partitions being the maximum.

The free space is indeed outside the extended partition.
However, there is no System Reserved partition. At least it is not detected and shown by either gparted or Easeus partition master which I use in Windows.

But why am I not able to make my home and swap as logical partitions? The option itself is not available. I get the primary or logical partition option only for the first partition I make (root)

---

### Post by Quackers on 2011-07-25
You can make all 3 partitions (root,home and swap) logical but first you will need to extend the extended partition to the end of the disc - gparted will do that. Then the free space will be inside the extended partition and you can create logical partitions all day :-)

---

### Post by ~!geek!~ on 2011-07-25
> **vjpotter said:**
> The free space is indeed outside the extended partition.
However, there is no System Reserved partition. At least it is not detected and shown by either gparted or Easeus partition master which I use in Windows.

But why am I not able to make my home and swap as logical partitions? The option itself is not available. I get the primary or logical partition option only for the first partition I make (root)


The way I understand partition thing: Its like you can't have 4 primary partitions on a hard disk (The extended partition is also counted as a primary partition.).
After doing this 3 primary partition + 1 extended(primary) partition, you cant free up space and try to create new partitions. Also, logical partitions can only be created as a part of the one extended partition, I hope.

---

### Post by Quackers on 2011-07-25
Correct except for a small correction in your first line.
You can't have MORE than 4 primary partitions on any mbr partitioned disc. The maximum of 4 can include one extended partition (so 3 primarys plus one extended).

---

