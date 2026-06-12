---
title: "installing a new sata drive"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by JJCool34 on 2011-08-10
Purchased a Sabrent 4 port sata pci host card and a 320GB western digital sata hard drive.


Installed PCI card fine and I can see it in the Disk Utility, cannot see the hard drive that I connected with the sata cable and sata power cable.  Need help please.  I am new to Ubuntu/Linux but I am very computer literate.

---

### Post by dino99 on 2011-08-11
is that new hdd seen by bios ?
maybe check the motherboard doc or the pci card doc too.

can you boot with ubuntu ?
if you can, then run:
sudo update-pciids & update-usbids
sudo blkid
(this might list the hdds uuid)

---

