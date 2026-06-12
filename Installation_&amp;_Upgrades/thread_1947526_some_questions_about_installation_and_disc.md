---
title: "some questions about installation and disc"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by zzzubu on 2012-03-26
sorry for my poor english...

1. does grub must be installed in primary partition ?
2. does OS like windows or linux must be installed in primary partition?
3. i have set 8 partitions in sda,when i install the OS,i just amout 3 of them,so the question is that do the 5 left will be wasted?
4. in linux,how to modify the computer's name?
5. how to set vmWare to have the ability to access the real physical machine's clipboard ?
6. in a disc-to-disc copy,does the mbr will be copy too?
7. what is a recycle device ?

---

### Post by zzzubu on 2012-03-27
................

---

### Post by Mark Phelps on 2012-03-29
Perhaps the reason you've not got a response sooner is that these All-in-One unrelated question threads don't do well here.  You would do MUCH better if you post a thread for each problem  especially since these are unrelated.

But, two answer some partition-related questions:
1) GRUB does not have to be installed to a Primary partition; it will work fine in a Logical partition.
2) Windows OS needs to be installed to a Primary partition, and to make things easier, if you're installing both MS Windows and Ubuntu, each to their own partitions, install MS Windows first.
3) Using traditional partitioning. 4 Primary (or 3 Primary and one Extended) are all the partitions allowed.  If you are using something like GPT or UEFI BIOS, I am unfamiliar with those and can not answer your questions.
4) With Ubuntu, you really only NEED two partitions: one for the OS, another for SWAP.
5) MBRs don't get copied as they are unique to each physical drive -- and outside the partition space.

Please post new threads for your other questions.  thanks

---

