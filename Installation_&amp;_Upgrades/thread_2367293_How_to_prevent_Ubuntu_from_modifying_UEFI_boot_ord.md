---
title: "How to prevent Ubuntu from modifying UEFI boot order"
date: 2017-07-28
forum: Installation &amp; Upgrades
---

### Post by sbcontt on 2017-07-28
I am used to choosing OS via BIOS boot selection menu, not grub. My laptop has two hard drives: each with their own bootloader. I have set the boot order in UEFI to boot Windows by default. However, each time I load Kubuntu, it sets itself as the default boot entry. Is there any way to prevent Kubuntu from being an idiot?

---

### Post by sbcontt on 2017-07-28
is it possible to achieve this by mounting efivarfs read-only?

---

### Post by oldfred on 2017-07-28
Are both installs UEFI?
If you are switching to BIOS mode, then it may be defaulting to that.

Post this:
sudo efibootmgr -v
sudo parted -l

What brand/model system? Many seem to want to make Windows default in all cases.

---

### Post by sbcontt on 2017-07-28
Thx for your response.

Yes both installations are in UEFI mode. It is a HP ProBook 440 G1. Fortunately I have been able to resolve this problem in the meantime by simply deleting the Windows Boot Manager entry from GRUB. Now Ubuntu is not trying to rearrange the boot order anymore.

---

