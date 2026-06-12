---
title: "problems installing ubuntu: installation stops unexpectedly"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by gnaump on 2006-03-05
when installing ubuntu 5.10 from cd the starting site's graphical appearance is in very bad shape :( but I can read that I have to push <enter> to start standard installation. -> installation starts :) , but it stops at the line:
[4294672.447000] ata1: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48 :( 

Can someone tell me what's the problem? :confused:

---

### Post by evilghost on 2006-03-05
Try the "noapic nolapic" arguments during installation, or even "noapic nolapic acpi=off pci=noacpi"

---

