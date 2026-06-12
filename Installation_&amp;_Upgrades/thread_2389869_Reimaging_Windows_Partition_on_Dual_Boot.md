---
title: "Reimaging Windows Partition on Dual Boot"
date: 2018-04-22
forum: Installation &amp; Upgrades
---

### Post by vincentertainment on 2018-04-22
Hello,
I'm planning on reimaging my Win 10 partition on a laptop that I dual boot with Ubuntu 17.10. Will Windows respect my current boot config or should I back up GRUB and bootloaders?
If so, what's the process for backup and restoration? There is no separate boot partition if that matters.
Thanks

---

### Post by Mark Phelps on 2018-04-22
Difficult question to answer because you've provided no details about what is in the image.

Depending on what tool you used to create the image, and what partitions you included in that image, it may (or may NOT) include boot/loader files and or partition.

IF it does, when you then load that to the drive, after that, it will boot by default into Windows.

IF it does not, then it will not boot into Windows, as the image you loaded does not contain a Windows boot partition.

Additionally, if the drive is configured using UEFI, that presents a whole different set of problems -- one that I am not able to resolve.

---

### Post by vincentertainment on 2018-04-22
Thanks Mark.
I'm not sure what additional image details would be helpful.
 My laptop is UEFI. I'd be using the current Windows Installer for build 1709. My Windows Boot Manager is currently on dev/sdb2. I've added Ubuntu to PCs with Windows several times but never installed (or reinstalled Windows) alongside an existing Ubuntu partition. I've heard that Windows doesn't play as nicely as Linux in dual-boot scenarios so its usually best to start with Windows.

---

### Post by yancek on 2018-04-22
If you are using windows 10 and UEFI, you will have a separate efi partition which will contain windows efi files in a Microsoft directory and Ubuntu efi files in an ubuntu directory on the same partition.  Your other windows boot files (BCD, bootmgr, winload.exe) will be on your windows system partition which apparently is what you want to back up.  If you are simply backing up the windows system prtition (often referred to as the C:\ drive) you should have no problem as long as you restore it correctly to the same partition.  I would suggest that you verify that you are using UEFI on both windows and UBuntu.

What software were you planning to use to back up the windows system partition?  I would recommend that since you are doing only windows, you use windows software and try to get advice from a windows forum.

---

