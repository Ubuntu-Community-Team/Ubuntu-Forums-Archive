---
title: "No Boot  - 11.10 install on Asus EFI BIOS"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2012-01-11
I am installing 11.10 on an Asus P8H61-M LE motherboard.

The OS would install OK with no errors but would not boot.I thought I had the same problems with UEFI Bios and GRUB that many other people have had.

After many reinstalls and various partition schemes,I found that the SATA configuration needed to be changed.
I am using a WD160 GB IDE drive with a SATA converter attached.
I think the BIOS may have been confused by this and set the wrong defaults even though it does see the drive.
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

After doing this the standard automated Ubuntu installation booted fine.

---

### Post by jruden on 2012-03-21
Hmm interesting. I have recently acquired an Asus bare bone box with p8h67 and have a similar problem. At the moment I am getting "Read error" with grub2 tries to boot. I will try this enable setting you mention.

---

### Post by jruden on 2012-03-22
Nah, this didn't do the trick for me. I have some other problem. And my box have 3 hard drives and the grub one is an SSD.

---

