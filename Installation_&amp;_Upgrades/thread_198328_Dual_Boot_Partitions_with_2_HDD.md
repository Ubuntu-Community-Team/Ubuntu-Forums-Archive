---
title: "Dual Boot Partitions with 2 HDD"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by habakkuk on 2006-06-17
My PC has two hard disks; the first (C) has all my Windows XP stuff, and the second (D) is basically empty. Will the LiveCD partition this second disk without mucking up the C: drive, and give me the choice of which OS to boot to? The second disk is about 40GB, and I would like to keep about half of this for NTFS use if I need it later.

---

### Post by aysiu on 2006-06-17
The Desktop CD (the live/installer one) won't automatically install it to what you're calling D:, but you will have that option.

You'll have to select **manually edit the partition table**.

The next screen will be a partition summary screen--you should create a small swap partition and the rest of the space on D: should be formatted as Ext3.

The screen afterwards will let you choose mount points. 
The large Ext3 partition should be marked for reformat and mounted at /
The swap partition should be mounted a swap.

NTFS on that drive will be virtually useless to Ubuntu, as it will be read-only. It's far better to make it Ext3, and then use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write the Ext3 partition from Windows XP.

For more details, including screenshots of what I'm talking about:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by rcarring on 2006-06-17
The / ext3 partition should be Primary, as well as the swap.

Since you are only using the second hard disk for Ubuntu aysiu's comments regarding ntfs make sense so long as you don't intend putting huge data files on the drive. I have every confidence in the ability of the driver they mention, but please read any info regarding the driver on site to make sure that whatever you do decide to put on the second disk and run from windows won't give rise to a problem.

One suggestion: if the second disk goes ext3 and swap, maybe creating a folder called 'NTFS' or 'Windows' would help you corral XP files if written to the second disk.

---

### Post by habakkuk on 2006-06-17
Thanks, completed the installation using the partitioning you suggested.

---

