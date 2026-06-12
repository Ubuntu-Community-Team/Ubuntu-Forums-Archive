---
title: "Dual BIOS boot Encrypted Kubuntu + Win10"
date: 2018-10-06
forum: Installation &amp; Upgrades
---

### Post by sean-1985 on 2018-10-06
Hi,
I have a usb memory and would like to install both Encrypted linux and windows (Dual BIOS boot Kubuntu + Win10) on it, as a portable system device.

I already have windows-to-go installed on it successfully, but I am having trouble installing encrypted Kubuntu.
I would like to encrypt as much as I can (ideally including the /boot).
 I am using BIOS boot instead of UEFI and I would like to use the windows boot loader to manage both window and linux boot (sometimes the windows upgrade depends on that).

I am having trouble with this setup. I found some information about setting up with UEFI ([https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcess](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcess)), but didn't get very far. Especially, I don't know where to install the grub, so that I can later add it into the windows bootloader using easyBcd.

Anyone has any idea how to do this?

---

### Post by yancek on 2018-10-06
If you want to use the windows boot loader and the windows software EasyBCD, you would be much better off asking your question at a windows forum.

I'm not sure an encrypted boot partition will work, might have to investigate that further.

---

### Post by sean-1985 on 2018-10-06
thanks but I am waiting for some practical solutions

---

