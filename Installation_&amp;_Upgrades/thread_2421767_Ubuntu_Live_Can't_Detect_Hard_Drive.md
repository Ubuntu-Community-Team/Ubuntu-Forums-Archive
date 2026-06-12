---
title: "Ubuntu Live Can't Detect Hard Drive"
date: 2019-06-26
forum: Installation &amp; Upgrades
---

### Post by foob99 on 2019-06-26
Hi, I have been trying to install Ubuntu on my Dell Inspiron 15 7000 for four days. I believe where the problem lies is that Ubuntu cannot detect my hard drive. Whenever I choose the installation type, no device appears in the table. Furthermore, the button where you add a new partition, "New Partition Table...", is greyed out. I have searched thoroughly throughout multiple forums on how to fix this and nothing has worked.

When I open up GParted, it only shows the USB I have to boot Ubuntu. What should I do to fix this? I don't believe this is a hardware issue, as this laptop I have is almost brand new. 

Here is a link to a screenshot of what GParted looks like and what the installation looks like.
[https://ibb.co/X5yZDdX](https://ibb.co/X5yZDdX)

---

### Post by Dennis N on 2019-06-26
General suggestions that might help:
Disable fast startup in Windows.
Disable secure boot in UEFI firmware.
Ubuntu must be installed in UEFI mode, as Windows 10 is. You must boot the USB installer in UEFI mode to do a UEFI installation.

---

### Post by foob99 on 2019-06-26
Thanks so much for helping. I apologize for not mentioning this, but while trying to install Ubuntu, Windows was deleted. Also, I have always been booting in UEFI and I have secure boot disabled. I have tried doing a BIOS boot and have had the same results.

---

### Post by Dennis N on 2019-06-26
Check to be sure RAID is disabled in your UEFI firmware.

---

