---
title: "Unable to install GRUB in /dev/nvme0n1"
date: 2024-03-01
forum: Installation &amp; Upgrades
---

### Post by melidonis on 2024-03-01
I used this instructions ([https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)) 2 years ago to setup my current pc (Ubuntu Desktop 22.04) without any problems.   
     Now I have tried the same instructions to setup a new pc but I keep getting an error.   
     "Unable to install GRUB in /dev/nvme0n1. Executing grub-install /dev/nvme0n1 failed.   
     The hardware of the 2 pcs are identical. I also tried with a new disk in my working pc, but still the same error.   
     Any ideas what I'm doing wrong?

---

### Post by yancek on 2024-03-01
Does the new computer have only one hard drive and is that drive blank?  Which option did you select for the install, Erase disk and install or a different option?  Is the new computer an EFI capable computer?  Did you boot and install in EFI mode or Legacy?  Did you go through the process explained on that page to "Enable encrypted Grub"?  I don't use LVM or encryption so you will have to wait for someone else familiar with both to post.

---

