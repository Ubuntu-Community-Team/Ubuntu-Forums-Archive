---
title: "External Hard drive for Linux/Windows storage only"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by Saponsky09 on 2007-08-12
I want to install Feisty on my laptop's internal hard drive, I will partition my drive so I will run Vista and Feisty from the hard drive.  The thing is that I have an external hard drive and I want to use it for storage only.  How do I format my external hard drive so I can dedicate one partition for Window's storage and another partition for Linux? Is it possible?
I believe it's possible though I don't imagine how the OS will know which partition to moun or recognise or something. Tanx for any help.

---

### Post by merlinus on 2007-08-12
You can format the external as ext3 and install fs-driver so windows can write to it.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by Saponsky09 on 2007-08-12
Thanks for the link man. Another thing is,will the partition manager from Feisty erase anything from Windows or will it do everything in the free space of the hard drive? Anyways I have a backup but I hate installing everything again. :confused:

---

### Post by merlinus on 2007-08-12
You will need to use vista's disk manager to shrink its partition.  Beforehand, delete temp and other unneeded files, backup data (which you seem to have already done), set virtual paging to zero (you can set it back again after installing ubuntu), and defrag several times.

Then make sure at the install partitioning screen to use contiguous free space, NOT the entire disk.

-merlin

---

