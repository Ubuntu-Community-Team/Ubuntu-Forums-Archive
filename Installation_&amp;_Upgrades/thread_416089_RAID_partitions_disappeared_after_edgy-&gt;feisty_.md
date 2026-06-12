---
title: "RAID partitions disappeared after edgy-&gt;feisty upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ifinishwhatistar on 2007-04-20
A few hours ago, I had a functioning Edgy system, using a RAID 0 software raid array through dmraid, using the nvidia controller.  I upgraded to Feisty using "update-manager -c -d," and now the system won't boot.  It gives me the error that "Alert /dev/mapper/nvidia_bfcfchfc4 doesn't exist."  where nvidia_bfcfchfc4 is my root drive.  

Then it drops me to the afs shell.  From there I have tried dmraid -ay, which tells me that the controller/drive itself (nvidia_bfcfchfc) is loaded, but doesn't list any of the partitions.  I have started up off of an old live cd, and indeed from there dmraid can still identify my 4 partitions (windows, boot, swap, and root) without a problem.

Why has upgrading to Feisty made my dmraid dysfunctional?  How can I boot my system?

---

### Post by ifinishwhatistar on 2007-04-20
Incidentally, booting the 2.6.17-11 kernel works, just not the new one...any ideas?

---

