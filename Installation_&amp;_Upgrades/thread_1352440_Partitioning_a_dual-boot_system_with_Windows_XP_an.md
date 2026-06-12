---
title: "Partitioning a dual-boot system with Windows XP and Ubuntu 9.04"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by AndrewAllen on 2009-12-11
I'm trying to set up a dual-boot installation with Ubuntu 9.04 in a partition on my Dell laptop with a hard-drive of about 70 Gbytes, having previously installed Windows XP in a 20 Gbyte partition. I'm using gparted to partition the drive and have now formatted the other 50 Gbyte partiton as ext3 filesystem for linux, thinking that the ubuntu installer would use this whole space for the installation. However, when the ubuntu installation process comes to the partition stage, it doesn't automatically pick up the fact that it should use the 50 Gbyte ext3 partiton, which is pretty infuriating! So I have to get into the business of trying to partition manually, specifying boot and swap partitons etc, which is really above my level of expertise, ie I have no idea what values to specify for these (and the process is NOT user-friendly!). Has anybody else encountered this problem and is there a nice simple solution - or can you please give me the values to use for the manual partitioning process?
Thanks, Andy

---

### Post by darkod on 2009-12-11
> **AndrewAllen said:**
> I'm trying to set up a dual-boot installation with Ubuntu 9.04 in a partition on my Dell laptop with a hard-drive of about 70 Gbytes, having previously installed Windows XP in a 20 Gbyte partition. I'm using gparted to partition the drive and have now formatted the other 50 Gbyte partiton as ext3 filesystem for linux, thinking that the ubuntu installer would use this whole space for the installation. However, when the ubuntu installation process comes to the partition stage, it doesn't automatically pick up the fact that it should use the 50 Gbyte ext3 partiton, which is pretty infuriating! So I have to get into the business of trying to partition manually, specifying boot and swap partitons etc, which is really above my level of expertise, ie I have no idea what values to specify for these (and the process is NOT user-friendly!). Has anybody else encountered this problem and is there a nice simple solution - or can you please give me the values to use for the manual partitioning process?
Thanks, Andy

It's very logical in fact. Since you already created existing partition, Ubuntu can't know why is it there, and it can't really delete it and put itself on it because you might have data.
The easiest way is to use Gparted again and delete that 50GB partition. It will convert to unallocated space, and that's what you need in fact.
Then when starting the installer tell it to Use Largest Continuous Free space, and that's it. Alternatively, after deleting the partition you can create your own partitions for Ubuntu using the installer partitioner manually, if you want. Note that you need at least two, / and swap.

---

