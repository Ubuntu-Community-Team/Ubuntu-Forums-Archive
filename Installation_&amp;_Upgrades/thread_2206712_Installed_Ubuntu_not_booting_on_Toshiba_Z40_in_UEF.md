---
title: "Installed Ubuntu not booting on Toshiba Z40 in UEFI"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by mauro3 on 2014-02-20
Hi all,

This is my first post so please excuse me for any mistake I might make going forward.

I installed Ubuntu 13.10 on a Toshiba Tecra Z40 booting in UEFI mode.
The installation went well but no OS booted (I've only Ubuntu installed) so tried boot repair in "Recommended repair" mode, followed all the steps but still no OS booted at the next time
The pastebin is [http://paste.ubuntu.com/6963861/](http://paste.ubuntu.com/6963861/)

Since it didn't work I went ahead and read all the forums I could find and decided to give it a shot with "Advanced options", unfortunately no luck there either
The pastebin is [http://paste.ubuntu.com/6965385/](http://paste.ubuntu.com/6965385/)

Any idea how I can move forward? I intend to use only Ubuntu on this laptop so I can delete and reinstall pretty much anytime for now (since the laptop is useless ;-)

Thanks,
Mauro

---

### Post by mauro3 on 2014-02-20
I think I made some progress, using Boot Repair with Advanced Option I removed "Secure Boot" (since I've it disabled from the BIOS too) and enabled the grub menu to show up for a few seconds.
Now I can see the grub screen and pick up "Ubuntu" from the list, unfortunately it seems something graphical goes wrong as I get

[drm:drm_pci_agp_init] *ERROR* Cannot initialize the agpgart module.
DRM: Fill_in_dev failed.

I tried removing nomodeset from grub but it didn't help :-(

---

### Post by mauro3 on 2014-02-20
Dropping nomodeset from grub config file seems to have fixed it :P

---

