---
title: "Installing on a HP which as already 4 primary partitions"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Theobalt on 2010-12-03
Hi!

I want to install ubuntu on my new hp laptop (dual boot with the already existing windows 7), but there is already 4 primary partition. So, I cannot create another partition for ubuntu using gparted. 

Someone already had this problem?

---

### Post by Quackers on 2010-12-04
You will need to delete a partition after backing up what is in it. Then create an extended partition, within which you can have as many new partitions as you like.

---

### Post by Theobalt on 2010-12-04
I hoped there could be some other mean. But why is it limited to only four?

---

### Post by Quackers on 2010-12-04
I think it is the limit set by the MBR partition system.
NB You only need to delete a partition temporarily. After creating an extended partition you can put the data back on to a newly created logical partition and then create further new partitions for other operating system installations.
Backup the data on the partition you are going to delete, then replace it afterwards. But make sure you can copy all of the data. For example some recovery partitions may have hidden data which may not be copied or image files that cannot be seen.

---

