---
title: "Repartitioning SATA prior to install"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by darkaudit on 2006-07-07
My installation setup has both an IDE and a SATA drive. In Windows, the SATA drive is the My Documents folder.

I have the IDE drive set up for the root partition. I'd like to split the SATA drive into two partitions, one Windows, and the other /home.

Unfortunately, the Kubuntu installer will only allow me to use all or none of the SATA drive. I cannot resize the partition.

I booted without changing any options other than the screen size. Is there a switch that I may have overlooked when booting?

---

### Post by Sonofmoog on 2006-07-07
If your Windows filesystem is NTFS, you may be out of luck.  Linux partitioners are supposed to be able to resize NTFS volumes, but I've never tried it, and don't recommend it.  For Windows file systems, use Windows tools.  That means Partition Magic or another partitioner.

I don't know what software you have available, but on the odd chance you have Norton Ghost, you could backup the Windows partition to a CD-R (better, vacant space on the IDE if there is any), then run Kubuntu install , create both drives on the SATA, then restore the Windows image ..

---

### Post by darkaudit on 2006-07-07
A little deeper searching in the forums found a link to BootItNG. I was able to resize the NTFS partition to make room for /home. Now to go back and try the installation again. :)

---

