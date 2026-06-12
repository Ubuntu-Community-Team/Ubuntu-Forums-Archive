---
title: "Windows Vista and Ubuntu 8.10 on two hard drives, How to increase partition?"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by praom2104 on 2010-04-09
Hi, 
I installed ubuntu 8.10 in a 80GB HDD
In hurry i also installed Windows Vista in a 160GB HDD.(By removing the 80GB cable)
I love using linux for most cases and i wish to increase the space by another 60 GB. Is there any possible way to do it.

What i really require is Ubuntu in 140GB and Vista in 100GB.
Kindly help me.

Note: At present i open the case, change cables and boot. I feel it very difficult.

---

### Post by oldfred on 2010-04-09
You should not have to switch cables, but some settings may be set as sda so if both drives are installed you may have to update grub & fstab to use UUID or corrected drives.

I have gone the other way and now have 3 Ubuntus installed each in a 20GB partition but have /home and /data in separate partitions. The root install then does not have to be very large and the home or data are the large partitions.

Install the windows drive as the primary master and the Ubuntu as the secondary master or slave if IDE or if SATA set the windows drive as the lowest connection number. Then run this script to see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

