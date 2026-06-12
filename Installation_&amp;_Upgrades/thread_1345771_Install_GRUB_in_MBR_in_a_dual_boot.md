---
title: "Install GRUB in MBR in a dual boot?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by donofrij on 2009-12-04
When installing Ubuntu on a 2nd partition as a dual boot to an existing Windows partition, I have read (extensively) and found two opposite recommendations concerning installing GRUB. One, is to install the GRUB to the MBR on the disk (default). The other recommendation was to absolutely NOT install GRUB in the MBR. Rather, make a mount point for a shared (FAT 32) partition; mount that  partition; this creats a file that Windows can use to boot Linux. Following reboot, a "ubuntu.bin" file appears on the FAT32 partition. Then copy this file to the c:\ directory and add it to the c:\boot.ini file.

Option 2 seems complicated, with inherent risks. Is it necessary. What is the downside to using the default option (installing GRUB on MBR?. Any advice, recommendations, instructions would be most helpful. Thanks

---

### Post by phillw on 2009-12-04
Hi

Option 2 does sound complicated !!!

I'd just pop it on as your bootloader on your MBR. It will 'see' your windows area and automatically let you boot to it, or ubuntu when you boot.

Phill.

---

