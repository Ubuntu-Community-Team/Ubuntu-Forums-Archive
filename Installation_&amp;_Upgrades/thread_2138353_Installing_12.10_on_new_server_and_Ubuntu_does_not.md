---
title: "Installing 12.10 on new server and Ubuntu does not detect the hard drives."
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by FloridaGuy on 2013-04-23
Went to install Ubuntu today on a just built server but the install only detects 1 drive. the server has a total of 5 drives 1 is a standard ATA drive and the other 4 are Sata drives. The drive are seen in the bios but not in Ubuntu. The ATA drive is going to be the Operating system and the other 4 I want to configure in a raid array. any suggestion on how to get Ubuntu to detect the other drive?

---

### Post by Cheesemill on 2013-04-23
Are the 4 drives plugged directly into the motherboard or into an add-on card?

Can you give us your system specs please, especially the motherboard and any other drive controllers you may have.

---

### Post by FloridaGuy on 2013-04-23
The 4 Sata drives are connected directly to the motherboard. The motherboard is a XFX GeForce 8100,8200,8300 with integrated GeForce Graphics.

---

### Post by Cheesemill on 2013-04-23
Try going into your BIOS and changing the mode of the SATA ports, put it in AHCI mode if you can.

---

### Post by FloridaGuy on 2013-04-23
The only options that I can change in the BIOS for Sata drives are: LBA/Large Mode, Block (Multi-Sector Transfer), PIO Mode and DMA Mode and none of them have an option ACHI.

---

