---
title: "intall win 7 and ubuntu on 2 hd same pc"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by kompressorgpl on 2012-02-26
Hello! I have 2 HD on my pc and I wan´t to install a win 7 on one and ubuntu 11.10 on the other. How do I do that?

---

### Post by darkod on 2012-02-26
During the windows install and the ubuntu install, you can select the destination disk. It is very simple. Just make sure to make the ubuntu disk first in boot order in BIOS so that it loads grub2 bootloader because windows bootloader can't boot linux.

Do you have any specific question?

---

### Post by kompressorgpl on 2012-02-26
Hello! No! My problem was the grub. When i get home I will tried that! Thank's!!!

---

### Post by efflandt on 2012-02-26
Assuming the Win7 is already installed or installed first on the first drive, it is probably best to select Other during the partitioning part of install.  Then you can arrange partition(s) however you want on the second drive (minimally usually / and swap), and pay attention to the drop down list on that partitioning screen to put grub in mbr of second drive (usually /dev/sdb).  After install, go to CMOS setup during BIOS splash screen (usually F1 or F2 key) and change boot order to boot 2nd drive first.  Grub should be able to boot everything from there.  I boot Win7 and 10.10 on sda and 11.10 on sdb (all 64-bit) from 11.10's grub on sdb.

Note that if you have enough RAM and are not going to hibernate, you do not necessarily need swap (swap is NOT necessary for suspend).  If you will want to hibernate, swap needs to be at least as large as RAM.  My desktop PC has 8 GB RAM and cold booting from SSD is faster than waking from suspend or hibernate, so I have no swap.

---

