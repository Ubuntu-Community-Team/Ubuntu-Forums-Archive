---
title: "Sata problem on asus a8vx"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by alek66 on 2008-06-22
I am trying to install ubuntu studio on my desktop which has sata drives. It seems to be as if it doesnt recognize the sata disks at all.

It promts to choose some drivers to use it. I couldnt find mine. I also enable de sata rom on my bios hopping it would do it automatically but.... i am lost i dont know what to do.


any help would be hot.

---

### Post by jorgepeixoto on 2008-10-02
You may try the pci=nomsi boot parameter.

---

### Post by dabl on 2008-10-02
Also try setting the SATA mode to "AHCI" in BIOS.

---

### Post by shiker on 2009-02-01
thanks for the solution!:p, the pci=nomsi worked, I was using a dvdrw sata that worked after this, before, it couldn't detect what was on the sata connector, btw, I didn't change the ahci in bios, is configured as sata

---

### Post by deeflex on 2009-06-18
Yes the pci=nomsi worked for me too!

I changed it to AHCI though. Wonder if it will make any change after the install, to change it back to SATA?

---

