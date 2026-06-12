---
title: "Partition shrink in Windows 7"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by RawG on 2012-02-27
I have question regarding shrinking of partitions in Windows 7 !

I am unable to recover windows due corruption of OS. I have only single partition in which Win 7 is installed. Can I somehow shrink the partition to create Unallocated space to perform a parallel installation to save my data?

If yes, I wud really appreciate the answer ....

---

### Post by darkod on 2012-02-27
If copying your data is the only thing you need, first it's better to try burning a ubuntu cd, booting in live mode, and copying the data you want to external hdd, or similar.

Ubuntu can run in fully operational, live mode from the cd. And as long as it can open the win7 partition it can copy any files to external hdd or another internal hdd.

Shrinking of windows partitions should be done from windows, but since you can't boot it, in case you want to try, you can also shrink it with Gparted in ubuntu live mode.

But if the partition is readable in live mode, it's better to copy the data, make a new install, and move the data back.

---

### Post by RawG on 2012-02-27
Thank you for the response! I will try that let you know what worked for me!

---

### Post by Mark Phelps on 2012-02-28
You can download the ISO image of the free version of Partition Wizard, burn that to CD, boot from that -- and use that to shrink the Win7 OS partition.  Since it's an MS Windows-based app, it should be able to do the shrinkage without problems.

---

