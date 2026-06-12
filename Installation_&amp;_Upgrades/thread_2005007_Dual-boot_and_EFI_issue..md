---
title: "Dual-boot and EFI issue."
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by ahanabu on 2012-06-16
Im helping a friend deal with a dual-boot issue (Windows 7 and Ubuntu (Kubuntu) 12.4). He has a 64-bit Samsung laptop with 8GB and a Tb Disk. It came with Windows 7 and EFI with a 100Mb sda1 partition. He installed Ubuntu 12.4 and GRUB2 naturally pointed to both Ubuntu and Windows, but when he booted Windows, it said it had to do some recovery stuff and undid GRUB, hence no booting into Ubuntu. He reinstalled Ubuntu and it set up GRUB2 but this time no Windows boot entry. I went over to his place last week and installed the new boot-repair utility and ran it, which restored the Windows entry, but Windows doesn't boot because of an EFI issue (and until then I knew zero about EFI/UEFI). Boot-repair prints out a little window which gives some info about where EFI should point to, and this probably will solve the Windows boot issue, but this requires configuring I'm not familiar with. How to point GRUB2 and EFI boot to properly boot Windows 7? Thanks in advance.

---

### Post by YannBuntu on 2012-06-19
Duplicate of [http://ubuntuforums.org/showthread.php?t=2006403](http://ubuntuforums.org/showthread.php?t=2006403)

Please don't do this. It makes loose time to you and to people who help you.

---

### Post by Elfy on 2012-06-19
Thread closed. Please do not post duplicates, it dilutes community effort.

---

