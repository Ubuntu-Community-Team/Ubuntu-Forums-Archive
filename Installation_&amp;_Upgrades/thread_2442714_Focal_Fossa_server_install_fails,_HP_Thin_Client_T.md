---
title: "Focal Fossa server install fails, HP Thin Client T610"
date: 2020-05-06
forum: Installation &amp; Upgrades
---

### Post by x3ua on 2020-05-06
I found this, but not sure is it related
[https://bugs.launchpad.net/ubuntu/+source/shim-signed/+bug/1786090](https://bugs.launchpad.net/ubuntu/+source/shim-signed/+bug/1786090)

Install fails to "updating initramfs configuration"

No problems when installing Lubuntu or other Ubuntu with desktop.

---

### Post by x3ua on 2020-05-06
Had to disable EFI. With legacy installation works.

---

### Post by ActionParsnip on 2020-05-07
If its a single boot system, why use EFI at all?
Please update the bug with your findings.

---

### Post by CelticWarrior on 2020-05-07
> **ActionParsnip said:**
> If its a single boot system, why use EFI at all?
Please update the bug with your findings.

Such question would be logical some 10 years ago. Now it no longer is.
Legacy/CSM will disappear sooner than later as there are no longer any justification for keeping it around (any OS that doesn't support UEFI is now End of Life and shouldn't be used).
The newer the PC the higher are the chances for having issues with hardware initialization in Legacy/CSM mode.
Using Legacy/CSM mode in GPT drives implies creating an additional partition making this method as difficult or even more than the standard recommended UEFI mode for all UEFI hardware. And some newer types of drives, namely NVME, don't easily support if at all, BIOS/MBR.
Legacy as the name implies is something ancient, a reminiscence of the 1981 BIOS that persisted far longer than its "best before date". It's outdated, period.

---

