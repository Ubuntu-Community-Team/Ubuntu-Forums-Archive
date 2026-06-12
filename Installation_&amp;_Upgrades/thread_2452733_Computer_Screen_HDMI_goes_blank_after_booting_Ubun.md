---
title: "Computer Screen HDMI goes blank after booting Ubuntu Installer"
date: 2020-10-27
forum: Installation &amp; Upgrades
---

### Post by keith47 on 2020-10-27
When I put the USB installer with Ubuntu 20.10 on it and I select boot the USB device in UEFI the screen goes blank. This is not after the Ubuntu Installer displays the GRUB boot prompt but after I select UEFI boot from the computers boot menu. The computer power is on and the light on the USB Flash drive flashes. Anyone know how to fix this? I also have another Linux USB installer and the same things happens when I try to boot it. I looked around in the BIOS and can't find anything about the display. The Dell Optiplex 3010 I use has a VGA and HDMI output.

---

### Post by ActionParsnip on 2020-10-27
Is it the Intel GPU or do you have the optional AMD RADEON HD 7570 or AMD RADEON HD 7470
[https://www.dell.com/downloads/global/products/optix/en/dell_optiplex_3010_spec_sheet.pdf](https://www.dell.com/downloads/global/products/optix/en/dell_optiplex_3010_spec_sheet.pdf)

---

### Post by keith47 on 2020-10-27
I solved this by turning on the Legacy boot option in the BIOS.

---

