---
title: "Blank screen when trying to install - nomodeset kernel panic"
date: 2017-08-02
forum: Installation &amp; Upgrades
---

### Post by teoiovine on 2017-08-02
Hi people!
I've been trying to install Ubuntu 16.04 on my desktop but I can't  seem to make it work. I've tried both with USB and DVD (both checked for  intregrity) with no differences.  

The USB/DVD boots, and it shows the UEFI selection screen (try  Ubuntu, install, check disk, etc...). Whichever I choose, it goes  straigth to a *blank* screen.

  I've tried booting in BIOS (legacy) mode, and the only difference is I  don't get the selection screen, just a brief purple screen with the  little guy on the bottom, and then again, blank screen.

  I've also tried with the following grub boot methods: nomodeset,  nolapic, acpi=off, acpi_osi=(nothing after the =) and different combinations of them. Some combinations  shows some processes going on, but no luck, some of them go to a kernel  panic.

I've turned off secure boot, turned on IOMMU and tried different combinations of uefi or bios or whatever. The PC has only Windows 7 installed (I don't plan on keeping it) so there is no fast boot.

  Here are my specs: 
-Gigabyte Gigabyte GA-970A-D3P (no on-board video)
-AMD FX6300
-Sapphire RX460
-1TB WD


  Thank you!

---

