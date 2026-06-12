---
title: "Upgrade to 8.04 =&gt; Cannot find partitions...?"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by nkonstas on 2008-06-15
Hi,

after upgrading to 8.04 my md raid array stopped working. 

The device names are still the same (both sata, sda1 & sdb1) but if I use fdisk to examine their contents they appear to have no partitions...!

EDIT: fdisk displays the following warning on both partitions:
invalid flag 0x0000 of partition table 4

EDIT #2: booting the previous kernel seems to work ok. So I suspect the VIA driver...

EDIT #3: both sata drives are connected to a SiI 3114 4-port PCI card. Are there any issues with sata_sil in 8.04? The problem is discussed [here]("http://www.backports.ubuntuforums.org/showthread.php?t=331190") but there seems to be no solution... help...!!!

This is an EPIA motherboard with the via82cxxx chipset.

Any ideas?

[FINAL EDIT]
My mistake: the drive names have changed following the upgrade to 8.04. It all works fine now.

Thank you,
Nikos.

---

