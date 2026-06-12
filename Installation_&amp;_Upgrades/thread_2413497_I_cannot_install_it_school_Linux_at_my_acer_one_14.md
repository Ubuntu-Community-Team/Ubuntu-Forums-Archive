---
title: "I cannot install it school Linux at my acer one 14z422"
date: 2019-02-26
forum: Installation &amp; Upgrades
---

### Post by gs143 on 2019-02-26
acer one 14z422 AMD  I cannot install multiple os means windows 10 install next to it school Linux 14.4. I facing problem  windows install done as usual I have 100GB free space for Ubuntu but install ubuntu the partition time will show total HDD Space how can I install multiple os in this system

Anyone can help me

---

### Post by TheFu on 2019-02-26
Ubuntu 14.04 support ends in 2 months. Trying to install it now is a waste of time.  Work with 16.04 or 18.04.  Always stay with LTS release that are under support for systems you need to work.  The non-LTS versions don't have enough lifetime to be worth our use on important systems.

We need some facts to help. Can you boot ubuntu using a flash drive? If so, do that, then install "**boot-repair**" and run the information gathering part of that tool, then post the generated URL back here.  Having free space doesn't mean that space is available to any other OS.  That is my first guess for the issue. If there aren't 2 free partitions and at least 25G of unallocated storage.  That means it cannot be used by any other partitions.

In addition to the disk information the above tool will provide, the output from **inxi -Fz** would help with everything else about the computer, on an overview level.
 
Look for Oldfred's posts about Acer and UEFI in these forums. I vaguely remember something in the UEFI setup with their systems which was non-standard.

---

