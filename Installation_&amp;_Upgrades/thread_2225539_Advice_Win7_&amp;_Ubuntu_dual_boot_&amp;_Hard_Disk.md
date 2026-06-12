---
title: "Advice Win7 &amp; Ubuntu dual boot &amp; Hard Disk - best configuration"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by paullangdon678-1 on 2014-05-21
I have two hard drives: SSD (120Gb) and HDD (320 Gb).
Currently dual booting Win 7 & Ubuntu 14.04. All fine but my SSD drive is low on space. Plenty of room on HDD.
I am thinking remove Win 7 from the SSD and re-install on HDD. Is this the best approach and is this likely to be easy to achieve?
The bios on my laptop suggests I have UEFI although not enabled. Do notunderstns this fully and the configuration in the BIOS refers to windows 8.
Grateful for advice.

---

### Post by oldfred on 2014-05-22
Best to see details, post link to BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Both Windows and Ubuntu can be either UEFI or CSM/BIOS if hardware supports it. But always best to have both systems installed in same boot mode. And how you boot installer is how it installs, so always know which way you boot any install media.


 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

