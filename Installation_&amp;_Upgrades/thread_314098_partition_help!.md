---
title: "partition help!"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by rkakkar on 2006-12-07
i have a 80GB hdd. I plan to keep one partition of 3GB for ubuntu and the other for my data. basically one ext3 and one fat32 partition. but i heard that fat32 partitions should not be more than 32gb as its not recognized. is that true? in that case would i have to divide the remaining space (80-3) in partition of 32Gb each?

---

### Post by 23meg on 2006-12-07
> but i heard that fat32 partitions should not be more than 32gb as its not recognized. is that true?They can be much larger, but AFAIK Windows XP and 2000 can only format as large as 32gb. You should be able to use a larger partition if you create it with another tool than the Windows format utilities, such as Ubuntu's Gparted.

---

### Post by rkakkar on 2006-12-07
> **23meg said:**
> They can be much larger, but AFAIK Windows XP and 2000 can only format as large as 32gb. You should be able to use a larger partition if you create it with another tool than the Windows format utilities, such as Ubuntu's Gparted.

so you're saying that if i use gparted to create say, a 70GB, fat32 partition, windows will be able to read/write to it and detect it as 70GB even though it can only format upto 32GB?

---

### Post by 23meg on 2006-12-07
Yes.

---

