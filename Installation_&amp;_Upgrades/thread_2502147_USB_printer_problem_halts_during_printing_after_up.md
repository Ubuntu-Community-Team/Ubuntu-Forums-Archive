---
title: "USB printer problem: halts during printing after upgrade to 24.04"
date: 2024-11-03
forum: Installation &amp; Upgrades
---

### Post by gja on 2024-11-03
After upgrading to 24.04 my usb printer (HP Envy 5640) halted during printing with an error.

Fix was found here:
[https://linux-packages.com/ubuntu-24-04/package/printer-driver-all]("https://linux-packages.com/ubuntu-24-04/package/printer-driver-all")

Removed all printer packages:
sudo apt remove printer-driver-all 

Then cleaned:
 sudo apt autoclean && sudo apt autoremove 

Then reinstalled:
 sudo apt install printer-driver-all 

So far printing seems to work again for me.

---

