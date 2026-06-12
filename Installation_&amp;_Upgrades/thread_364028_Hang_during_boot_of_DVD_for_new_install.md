---
title: "Hang during boot of DVD for new install"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by audibiturbo on 2007-02-17
System has:
hdc: cdrom drive
hde: 320gb hard drive PATA

hde is Highpoint Rocket 100, hpt302, pci, ata100 two channel controller.

cd will boot if hard drive is hda

cd boots until it sees the hpt302; it shows hde as dma and hdf,g,h as pio
hde/f on ide2 and hdg/h on ide3.

it simply hangs there forever. the asus p3v4x motherboard integrated ide controllers are only 28 bit lba, not big enough for the 320gb drive. my intent is to install and run ubuntu on the drive attached to the primary/master of the highpoint controller = hde.

ubuntu cd: ubuntu-6.06.1-desktop-i386.iso

any ideas/thoughts?
jon

---

