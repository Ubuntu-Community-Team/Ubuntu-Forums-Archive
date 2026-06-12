---
title: "Confused with Partitions"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by mailers47 on 2013-12-01
Hi, I want to install ubuntu permanently on my pc. I have 2 hard drives. 1 is a 320gb SATA and 2nd is an old 80gb. I want to install ubuntu on the C partition of the 320gb drive. It's the same partition I have win 8 installed on. When I tried to install ubuntu so many options on partitions came up that I am confused. I don't want to lose my data while installing ubuntu. I have read that a clean install of ubuntu will wipe out all the hard drive, not just the partition. I just want to install it on my C drive without making any changes to other drives.

Please help me here. What information do you need?

---

### Post by papibe on 2013-12-01
Hi mailers47. Welcome to the forums ):P

I would recommend making the space for the installation using Windows itself, before even attempting the installation.

I'm not very familiar with Windows8, but Windows7 has a tool called 'Disk Management' that allows you to reduce, delete, and create partitions. It would be easier if you either delete an empty partition, or reduce the size of one used, and leave that space unformatted. This space will appears available (i.e. empty) to the installer, and it would avoid making a mistake by installing Ubuntu on a used Windows partition.

It is always recommended to backup your important files as a security measure (just in case).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by oldfred on 2013-12-01
In Windows a c: drive is not really a hard drive but a partition. A d: drive can be another partition on the same hard drive or another hard drive, so it can be confusing.
In Linux drives are sda, sdb etc and partitions are the numbers at the end or sda1, sda2, sdb1 etc. So you should add a partition as Linux need its own format usually ext4 that is not Windows format like NTFS. Windows will not read Linux formats but Linux reads NTFS formatted partitions. But better to have another separate data partition for NTFS for any data you may want to share.

Also with Windows 8, you must turn off the always on hibernation or fast boot:
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

