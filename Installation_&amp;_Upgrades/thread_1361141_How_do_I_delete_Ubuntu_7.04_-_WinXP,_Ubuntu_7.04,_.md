---
title: "How do I delete Ubuntu 7.04? - WinXP, Ubuntu 7.04, Ubuntu 9.1 on same HDD"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2009-12-21
I have 3 operating systems on one hard drive, each on a separate partition (4 partitions in total - 1 for each OS with the Linux OSs sharing a swap space).  How do I delete the Ubuntu 7.04 installation?  I thought I could just simply delete the partition, but worried about screwing up GRUB.  What's the best way to remove Ubuntu 7.04?

---

### Post by presence1960 on 2009-12-21
Before you go deleting a partition let's see exactly what is on your machine. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text

---

