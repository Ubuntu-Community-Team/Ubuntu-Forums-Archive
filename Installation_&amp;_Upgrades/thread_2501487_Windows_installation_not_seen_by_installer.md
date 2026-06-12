---
title: "Windows installation not seen by installer"
date: 2024-10-10
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2024-10-10
Acer Swift 3 - Windows 11.
The installer for Ubuntu 24.04 isn't giving me the option to install alongside Windows.
Fast Boot is disabled, and the Windows install is not encrypted.
How can I solve this?

---

### Post by nicolasdentremont on 2024-10-10
Does the installer see the drive that Windows is on at all? And did you make a partition for Ubuntu using the Windows utility before starting?

I also have an Acer laptop and I had to change the RST setting to AHCI in the BIOS menu before the Ubuntu installer could see the drive. If you have to do that you will have to make some changes in Windows as well otherwise it won't boot.

---

### Post by Gordonbp531 on 2024-10-11
Solved - had to perform CHKDSK on the Windows partition and then all proceeded normally.

---

