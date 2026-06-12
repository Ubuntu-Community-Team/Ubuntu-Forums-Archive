---
title: "moving from Kubuntu to another flavour."
date: 2022-12-29
forum: Installation &amp; Upgrades
---

### Post by rleibner on 2022-12-29
Hi,
I am testing different Ubuntu flavours on an old Lenovo Yoga-330.
I installed Kubuntu alongside with Win10. It works, but I want to compare vs Ubuntu-Mate.
So, I flashed a pendrive with the new iso and rebooted ...
Unfortunately the installed grub (2.06) does not recognize bootable pendrive ! :(   I've test it on my desktop PC and it boots OK.
My goal is to install Ubuntu-Mate on the same partition where Kubuntu is now, keeping the dual-bootable facility (Ubuntu / Win10).

Any clue?

Note: It is a fresh installation, no need to separate the /home location.

---

### Post by oldfred on 2022-12-29
You do not normally boot live installer from grub. 

You should be able to use UEFI boot menu, often f12 but varies by vendor to choose USB flash drive. If Windows is UEFI install be sure to boot in UEFI mode.

---

