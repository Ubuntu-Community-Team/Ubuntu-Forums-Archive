---
title: "Resize partition in Ubuntu 10.10?"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by apanton06 on 2011-02-25
Currently I am using Windows 7 and Ubuntu 10.10, using the windows boot loader to chainload (edited the boot menu to include Ubuntu).
I set up my partition table as:
/dev/sda1 - 269 GB (Windows Partition)
/dev/sda2 - 500MB (Linux boot partition)
/dev/sda3 - 230 GB Extended 
/dev/sda5 - 5 GB   (Swap Partition)
/dev/sda6 - 225 GB (Linux partition)

I roughly halved the HDD size (500GB) before install, leaving around 250 GB to create all the partitions for Ubuntu 10.10. Now I want to install Fedora 14 as well, how would I go about shrinking the linux partition size to create unallocated space for Fedora 14?

How would I do this in Disk Utility or GParted or is it better to do this in the Windows 7 disk management tool?

---

### Post by cristian.ene on 2011-02-25
> **apanton06 said:**
> Currently I am using Windows 7 and Ubuntu 10.10, using the windows boot loader to chainload (edited the boot menu to include Ubuntu).
I set up my partition table as:
/dev/sda1 - 269 GB (Windows Partition)
/dev/sda2 - 500MB (Linux boot partition)
/dev/sda3 - 230 GB Extended 
/dev/sda5 - 5 GB   (Swap Partition)
/dev/sda6 - 225 GB (Linux partition)

I roughly halved the HDD size (500GB) before install, leaving around 250 GB to create all the partitions for Ubuntu 10.10. Now I want to install Fedora 14 as well, how would I go about shrinking the linux partition size to create unallocated space for Fedora 14?

How would I do this in Disk Utility or GParted or is it better to do this in the Windows 7 disk management tool?


Don't!!!i messed with that too... and i managed to **** up my grub...now i have a bricked device! it won't boot from anyhthing

---

### Post by apanton06 on 2011-02-26
> **cristian.ene said:**
> Don't!!!i messed with that too... and i managed to **** up my grub...now i have a bricked device! it won't boot from anyhthing

What did you mess up? I was just looking for the best setup for a triple boot, I'm looking in to just adding more logical partitions under the extended if it works.

Or were you referring to chainloading, which has worked perfectly for me. It's a good solution and faster if you want to remove other OS and just use windows, going through and changing the MBR can just be extra, unnecessary work.

If you messed up your GRUB and can't boot, reformat the hard drive and go for a fresh install.

---

