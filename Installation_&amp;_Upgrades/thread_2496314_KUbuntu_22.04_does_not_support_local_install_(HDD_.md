---
title: "KUbuntu 22.04 does not support local install (HDD / SSD install)?"
date: 2024-03-23
forum: Installation &amp; Upgrades
---

### Post by sasamiya on 2024-03-23
Hi,
Steps to reproduce issue:
(1) On Microsoft Windows, use Disk Management to create a FAT32 (9GB) partition as letter E:\ on local SSD (GUID partition table)
(2) Use 7-zip to unzip the kubuntu-22.04-amd64.iso to E:\
(3) Reboot PC to BIOS Setup, select "Save & Exit - Boot Override", select "UEFI: M.2: KINGSTON, Partition 6" as boot device, then press Enter
(4) On GRUB menu, Select "Try or install KUbuntu"
(5) It cannot show KUbuntu installer or livecd screen
For example, NVME (M.2) SSD is I used, CPU is AMD 3400G, integrated GPU is used.
Windows 10/11 can use this way to execute local install.

---

