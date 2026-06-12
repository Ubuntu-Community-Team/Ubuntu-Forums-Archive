---
title: "Disk Utility doesn't work during installation"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by Flik Shen on 2010-06-28
Hi all,

I found it is impossible to format partition during Ubuntu 10.04 installation.
My storage configuration is as following.
1TB (500GB X 2) AHCI RAID 0 (it is said fake raid) and covers below 4 partitions.
/dev/mapper/pdc_dgbbagea1 9621688   5872752   3260168  65% /
/dev/mapper/pdc_dgbbagea4 945587172  95673304 802259056  11% /home
/dev/mapper/pdc_dgbbagea3 9698380   1363364   7846240  15% /opt
Partition 2 is swap partition and root partition is ext3 original.

Since there is no enough space for upgrading, I try to format root partition and install a complete pure new OS.
After I booting up system from Live or Alternative disk, I try to switch root partition from file system ext3 to ext4 and format it.
However, Formating process always get failed after couple trying.
Even I quit installation and use tools "Disk Utility" to check and adjust partition information.
It reports device is busy.

What should I do to solve this issue.

Thanks and best regards,
Flik

---

### Post by Flik Shen on 2010-06-28
Hi all,

I found solution for this.
1. Using Live CD to do installation.
2. switch file system from ext3 to ext4 and formatted.
3. Trigger installation from Live.

I really don't root cause of this issue, the solution works fine me to formatted in Live CD.

if any mistake i made, please collect me.

Thanks and best regards,
Flik

---

