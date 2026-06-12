---
title: "Ubuntu USB installer does not see SSD drive"
date: 2022-01-14
forum: Installation &amp; Upgrades
---

### Post by Richard-S on 2022-01-14
I have a new Acer Aspire TC 1600, with a 500 Gig SSD, a MVMe Kingston OM8PCP3512F AA. It currently has Windows 10 installed. I want to erase the drive and install Ubuntu 21.10

The Ubuntu USB stick boots and runs fine, but cannot see the SSD drive. Gparted finds only the USB stick.

Richard

---

### Post by VMC on 2022-01-14
From BIOS,find: **SATA Operation** and select **AHCI**.
See if that works.

---

### Post by Richard-S on 2022-01-14
Yes, I changed it to AHCI and now Win 10 won't boot (Yahoo! Good Riddance!) but Ubuntu can now see the drive.

Thank you.

Richard

---

