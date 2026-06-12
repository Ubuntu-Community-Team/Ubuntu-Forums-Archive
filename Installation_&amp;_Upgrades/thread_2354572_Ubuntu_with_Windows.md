---
title: "Ubuntu with Windows"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by fakebr0 on 2017-03-04
Hello everyone.
I have one SSD 120 GB and one HDD 1TB drives. I would like to have my Windows 10 on SSD, and Ubuntu on my HDD. But I would like my HDD to be also used as a drive for different data.
My question is, can I install Windows 10 on SSD, then split HDD to 50 GB partition and the rest for data and install Ubuntu on that 50 GB Partition? I want to have an option to choose which system 
I want to use while turning on my PC. From what I've heard I should install win 10 on SSD, uplug it and install Ubuntu on that second HDD drive. Is this correct? If you don't understand something
I will try to explain somehow. Thanks for everything.

---

### Post by wildmanne39 on 2017-03-04
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2017-03-04
If you plan to use GPT partitioning then you would need to use UEFI for windows.  If you install windows UEFI, you need to install Ubuntu UEFI.  With UEFI, there will be an EFI partition and boot files for both windows and Ubuntu will be placed in separate folders on this partition.  If you don't have the windows drive attached when you install Ubuntu this will of course not be possible.  I understand it is possible to have an EFI partition on each drive but I think this complicates the boot process.  I would suggest you read the Ubuntu documentation at the link below on dual booting windows 10 and Ubuntu UEFI for some basic information.  Someone else with more knowledge on EFI should be along to help.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2017-03-04
Welcome. Just a note. You're much better off having OSs on the SSD as its the fastest and using HDDs for data. That is the general way to go about it, although if you have a specific reason for doing otherwise ...

Whether they're both on the SSD or not, you're still going to need to understand what is happening with UEFI, as mentioned previously, before you go ahead and install.

Your Ubuntu install will be slower as a consequence of a hard drive install.

---

