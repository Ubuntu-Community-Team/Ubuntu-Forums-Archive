---
title: "AHCI Installation problem."
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by firefreak on 2010-01-25
Hi,

I wanted to try out the new 9.10 Ubuntu/Kubuntu but I cant even install it. 

I have 2 80Gb Intel SSD connected to my MSI 790FX GD70 mainboard. AHCI enabled in Bios. I have Windows 7 on one and I wish to install Ubuntu on the other one. My problem is that the Ubuntu installer sees the two disks as one 160gb partition.

I've tried some tip about disabling the ubuntu raid driver but that did not help. I then see the two drives as I should but then it cant make any changes or format the drive I want. I get to the point where I enter my login details and when i click next it says: "Failed to create a ext4-filesystem on partition nr. 1 on SCSI2 (0,0,0) (sdb)"

I used "Sudo dmraid -E -r /dev/sda" and the same on "sdb". Does not help.



Is there any solution to this?

---

