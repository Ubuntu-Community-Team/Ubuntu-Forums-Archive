---
title: "Fixed grub/bios issue after Lucid Lynx installation."
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by suilix on 2010-05-09
After I installed Lucid Lynx, I could only boot into "grub rescue". I solved my problem using fdisk's extended option to fix my partition order then reinstalling grub using the Lucid Lynx LiveCD. 

This worked because my disk partitions were in a specific condition and because my laptop's (Dell Inspiron 9300) bios has a 137GB limit and because I have installed a 160GB drive.

The history of my partitioning created logical partition names starting from sda1 to sda6 where sda1-sda5 were below the 137MB limit but sda6 was above the limit. This worked because sda6 was a swap partition that could be accessed by linux because it does not use the bios to locate partitions, methinks.

When I installed Lucid Lynx to an unallocated space beneath the 137GB bios limit, the partition manager assigned it and its swap the logical partition names sda7 and sda8, respectively. In physical order, everything should have been fine BUT, I believe grub and bios traverse the location using the *logical* ordering implied by sda1 through sda8, and in that order the new partitions were above the 137GB limit (or it may be that my sda6 partition was physically above 137GB and grub/bios could not get passed it to reach sda7 [Lucid Lynx]).

Obviously, my problem is related to a very specific hardware and partition history but it may help, if you have a grub boot issue, to think about the correcting the usually benign logical / physical partition ordering.

---

