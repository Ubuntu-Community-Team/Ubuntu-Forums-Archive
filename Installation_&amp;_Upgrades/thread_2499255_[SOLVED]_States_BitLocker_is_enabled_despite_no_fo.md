---
title: "[SOLVED] States BitLocker is enabled despite no form of encrytion being present"
date: 2024-07-20
forum: Installation &amp; Upgrades
---

### Post by tomcorteil on 2024-07-20
Hello,

I'm attempting to install Ubuntu 24.04 LTS on my Dell G7 7790 that previously ran Windows 11. When I go through installation, the installer states that BitLocker is enabled, despite checking Windows settings - it states neither standard encryption nor BitLocker is enabled.

---

### Post by currentshaft on 2024-07-21
Thanks for letting us know.

---

### Post by Rubi1200 on 2024-07-21
> **tomcorteil said:**
> Hello,

I'm attempting to install Ubuntu 24.04 LTS on my Dell G7 7790 that previously ran Windows 11. When I go through installation, the installer states that BitLocker is enabled, despite checking Windows settings - it states neither standard encryption nor BitLocker is enabled.

Are you intending to replace Windows with Ubuntu completely?

I can think of two options to try:
1. go to BIOS/UEFI and temporarily disable any TPM settings.
2. on the live Ubuntu USB, open GParted and delete all partitions/volumes then create a new GPT partition table

Start the installer and try again.

Any progress?

---

### Post by tomcorteil on 2024-07-22
Thanks! The second option worked. Ubuntu is installed!

---

### Post by Rubi1200 on 2024-07-22
Glad to hear it all worked out.

Enjoy the new install.

---

