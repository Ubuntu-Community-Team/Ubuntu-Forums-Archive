---
title: "problems of installing ubuntu 7.1 with windows"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by ryanskyer on 2007-11-01
Hi all,

I have a windows in my laptop, I am installing the ubuntu. I have windows in the C partition of 20 GB, and unlocated the rest of space (60GB). I am gonna install the Linux in this 60 GB free space.

I manully partitioned the space when installing ubuntu, I partition 10GB to mount root /, and 1.5GB as swap. Then the rest of space became unusable space. I am not able to partition the rest to mount /home. 

Please let me know what's the problem. thanks.

---

### Post by Pumalite on 2007-11-01
If using Vista, you have to use the Vista partitioner first.

---

### Post by ddrichardson on 2007-11-01
Are you sure you only have three partitions? Can you post the output of ```
sudo fdisk -l
```From a terminal?

I only ask because if you have a recovery partition or some such then you will have used up all four primary partitions and will need to create a logical.

---

