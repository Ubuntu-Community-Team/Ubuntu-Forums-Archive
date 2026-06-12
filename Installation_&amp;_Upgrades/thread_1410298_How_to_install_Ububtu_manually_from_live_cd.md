---
title: "How to install Ububtu manually from live cd?"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by TheWanderingMaverick on 2010-02-18
I am running a Dell Dimension 3000 and I intend to install Ubuntu on it. On it, there is a partition, Dell Utility Partition, which I am hesitant to overwrite. The main partition which I want to install Ubuntu on I formatted in ext4. I try to install Ubuntu from the live cd, but it won't allow me to strictly use the ext4 partition. It insists to either use the entire drive or to have me manually choose the partition. How would I go about doing that? I relatively new to Linux in general, and would really appreciate some help.

---

### Post by darkod on 2010-02-18
That is because Linux by default does not use existing partitions, even when it's ext4. You have to manually tell it to (Manual Partitioning). But usually you would also use a swap partition, which means 2 partitions, not one.

You can:
1. Delete that partition you created and leave the space as unallocated. Then in step 4 tell the installer to Use Largest Available Free space (in other words, the space you left unallocated). It will create the default root + swap install.

2. Go into manual partitioning, delete the ext4 partition, in its place create smaller logical swap partition with mount point swap, it can be 2GB or the size of your ram if you plan to hibernate regularly. Then in the rest of the unallocated space create logical ext4 partition, mount point /.

That should be it.

---

### Post by TheWanderingMaverick on 2010-02-20
Thank you. That worked perfectly!

---

