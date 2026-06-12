---
title: "Ubuntu 10.10 install problems - extended partitions"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by gpsmikey on 2011-03-03
Greetings all - I seem to have discovered a "feature" - I was trying to install the server edition and when I put the root partition in an extended partition on the hard drive, it indicated the install was successful (and no error messages), however, it was unbootable.  I had partitioned the disk previously the way I wanted it, used the manual partition selection during the install and told the installer to put GRUB in the root partition (residing in the extended partition).  What we have found is that for some reason, the installer is MOVING the extended partition (not the partitions in it, but the main extended partition gets moved - up to 60 some sectors in several cases).  Several people over in the Terabyteunlimited.com (BING) forums have been able to replicate this.  I would NEVER expect the installer to move a container (extended partition) once it has been set up - especially without telling the user.  Installing GRUB to a primary partition works fine - only when there is an extended partition does this seem to happen.

mikey

---

