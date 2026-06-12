---
title: "Won't boot with SATA drives"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by fbp90crx on 2008-10-25
I am trying to load ubuntu on a computer with 3 SATA HDs, and anytime I build a partition and try to boot after it is installed, it sits on a BIOS screen saying it verifying boot something, not sure what exactly. But how can I install Ubuntu onto SATA drives.
I don't know if is necessary but the specs are
Intel Core 2 quad Q 6600
EVGA Nvidia 780i motherboard
BFG 9800 gtx
4 gig OCZ 800mH Ram pc2 6400
2 western digital [750gb and 500gb]
1 Hitachi 400 gb

---

### Post by bulldog on 2008-10-25
Choose which hdd you want to install ubuntu.
Look in your BIOS and set this hdd as the first boot device.
Install ubuntu on this drive and GRUB will be installed on this hdd at the end of the install procedure.
Reboot and it should work fine.

If you have an IDE hdd connected beside the SATA hdd's the story will be a little different though.

---

