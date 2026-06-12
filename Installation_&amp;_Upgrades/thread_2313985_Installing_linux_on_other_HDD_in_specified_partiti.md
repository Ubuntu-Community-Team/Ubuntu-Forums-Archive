---
title: "Installing linux on other HDD in specified partition"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by laisut on 2016-02-17
[SIZE=1]Hello, I am a developer - programmer and recently started coding in PHP. For a PHP programmer it is way better to have linux than windows (for built-in servers).[/SIZE] I have windows installed on my C drive (it is a 120GB SSD drive). Also, I have attached a HDD to the system (3 partitions of HDD 750GB). On the C drive, where my windows is installed, i only try to keep system files. All of the programs are installed on HDD first partition (D). I have made a partition for linux OS (E). _**[SIZE=2]Question is [/SIZE]- can i install linux on (E) partition without losing data on my entire HDD ?**_ And if so, im quite certain, that there will be no menu to choose wether i want to boot windows or linux because they are on different drives. P.S. if this is possible, is there a brief guide how to do this?

Here is the image of what i am talking about : [http://www47.zippyshare.com/v/TQjUnsoc/file.html](http://www47.zippyshare.com/v/TQjUnsoc/file.html)

---

### Post by oldfred on 2016-02-17
First understand the difference between a "drive" and a partition.
Windows greatly confuses the issue as it calls both drives & partitions "drives". 
A "d:" drive in Windows can be another partition on the first hard drive, or another partition on the second hard drive.

Post this from Ubuntu live installer in live mode. Use terminal:
sudo parted -l
sudo fdisk -lu

If gpt partitioned for new UEFI systems, fdisk may not work.

You cannot install Ubuntu to a NTFS partition. And best not to create partitions with Windows as it often uses proprietary dynamic partitions rather than the more common primary, extended & logical partitions use with MBR(msdos) partitioning. 

If newer UEFI, it also uses the newer gpt partitioning and extra partitions are not normally an issue.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by laisut on 2016-02-17
Thank you for the answer. Now i tried to do the installation. Everything succeeded but there are two main issues: 1) The partition that i installed linux on has dissapeared (i can only observe it through "disk managment") and whenever i shut down linux they do not shut down, everything turns off but the image of the background keeps showing and the mashine will not turn off (the same issue was when i just tried booting linux from usb).

---

### Post by oldfred on 2016-02-17
Windows will not correctly see Linux partitions.

What brand/model system and what video card/chip?

Best to see details. You can install into Ubuntu live installer or download as its own live system.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

