---
title: "partitioning hdd for windows"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by arranskye on 2016-05-07
best way to delete all partitions on sata drive to install windows10.  The system is dual boot with ubuntu on an ssd 120GB drive and windows on a 500GB sata drive.

I think this can only be done by live gparted cd or live ubuntu dvd. Am I right in thinking that the OS cannot be in use for this to take place.

Then I want to partition and format ntfs 200GB for windows and 100GB for Zorin  Is it right that I dont have to format the unallocated space for zorin, just choose ext4

I am running ubuntu 14.04 on the SSD drive and I want to be sure that windows does not try to overwrite it. 

thanks

---

### Post by yancek on 2016-05-07
You cannot resize or delete or make changes to a mounted partition so you need to use a GParted CD or the Ubuntu install DVD/flash drive which has GParted on it.

If you want to install Zorin, you can either leave unallocated space or create a partition with an ext4 filesystem.

---

### Post by oldfred on 2016-05-08
Is system UEFI or BIOS?
And is Ubuntu installed in UEFI boot mode or BIOS boot mode?
Just be sure to install Widnows in same boot mode as Ubuntu.

And if BIOS make sure you set HDD as default boot drive in BIOS before install. Windows typically puts its 100MB boot partition on drive set as boot. And since it does not see Linux partitions, it may just overwrite the first 100MB on SSD if that is default boot drive.

---

