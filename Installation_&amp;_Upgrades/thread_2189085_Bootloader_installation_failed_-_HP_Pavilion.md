---
title: "Bootloader installation failed - HP Pavilion"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by qwikrazor87 on 2013-11-20
For the past few days I've been trying to install Ubuntu 64 bit onto my friend's HP Pavilion laptop but I can't figure out how to get past the bootloader installation issue, it says that it fails to install into /target/. I have installed Ubuntu 32 bit in legacy mode but the wifi network does not work at all.
The laptop previously had Windows 8.1 64 bit installed but now it's a clean slate.
I'd appreciate some help with this issue.
Thanks.

---

### Post by ubfan1 on 2013-11-20
Are you installing in UEFI mode or legacy (or compatibility) mode?  Is your hard disk still gpt partitioned or did you convert it to msdos partitioning?  What partitions are you using (an EFI paritition is necessary for uefi mode, a grub-bios partition for a gpt disk in legacy mode)?

---

### Post by qwikrazor87 on 2013-11-20
I'm trying to install Ubuntu 12.04.3 LTS 64 bit in UEFI mode with secure boot and legacy mode disabled.
The HD has been wiped clean with dd, the partitioning is done automatically by the live USB installer.
I check the bootloader partition made by the installer and it is an EFI partition.

Edit:
I successfully installed Ubuntu 13.10 64 bit with legacy mode enabled and secure boot disabled.

---

### Post by ubfan1 on 2013-11-20
That's good to hear.  I had started with 12.10, and it had significant problems, so I expect 12.04 had problems too.

---

