---
title: "Problem with Installationen. No root file system is defined?"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by germanix on 2013-10-24
I am attempting to instal Ubuntu 12.04 on a new laptop. This laptop has both an SSD (eSata) as well as a normal HDD in the main bay. The OS is to go to the SSD. This machine was ordered without any OS installed. (MSDos). I used the live disk and Gparted to format both disks to ext4. When I attempt to install on the SSD the installer does allow mw to choose which HDD I wish to install to. I choose the SSD and then get the following information:
"No root file system is defined. Please correct this from the partitioning menu."
I do not know how to proceed. Any assistance will be greatly appreciated. Thank you.

I found the problem. Forgot the mount point /.

---

