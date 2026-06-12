---
title: "Adding a new partition to ubuntu disk"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by chris_tikva on 2008-08-02
I want to add a new partition to my disk so I can install another instance of linux for experimental purposes. I've had a look at the disk using Gparted and it shows there are 3 partitions there already. sdb1. ext3, sdb2 extended and sdb5 swap. If I try to shrink the ext3 partition to make room I get an error. What is the correct way to make room on the disk for another installation? 

Thanks,

Chris

---

### Post by overdrank on 2008-08-02
> **chris_tikva said:**
> I want to add a new partition to my disk so I can install another instance of linux for experimental purposes. I've had a look at the disk using Gparted and it shows there are 3 partitions there already. sdb1. ext3, sdb2 extended and sdb5 swap. If I try to shrink the ext3 partition to make room I get an error. What is the correct way to make room on the disk for another installation? 

Thanks,

Chris

Hi and I believe the partition you are trying to shrink is a extended partition. What is the error you are receiving? If you could post a screen shot it may help.

---

### Post by mikewhatever on 2008-08-02
ext3 is linux file system, not a partition. Can you post the output of 
sudo fdisk -l.

---

### Post by chris_tikva on 2008-08-02
I've managed to get it working now. It seems that the system had grabbed the disk and wouldn't give it back. I'd tried to unmount it but it hadn't actually done so - despite the system I had booted into being on a different device. I got round it by booting first and plugging the disk in afterwards. Now I've managed to add another partition and install puppy onto it and add it to my grub menu. So that's progress...

Thanks,

Chris

---

