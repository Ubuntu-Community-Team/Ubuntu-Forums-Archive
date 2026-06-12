---
title: "how to load Ubuntu on Lenovo ThinkStation P330"
date: 2024-08-09
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2024-08-09
I need help on setting the BIOS or other workaround to install Ubuntu Unity 24.04 on a Lenovo ThinkStation P330 [P330 (1S)MT-m 30C7-000YUS S/N MJ086EFN].  BIOS is looking for USB devices other than conventional USB stick.

Thank you,

John

---

### Post by sports fan Matt on 2024-08-09
I think this is my problem as well, although I'm running a Thinkpad T470.

---

### Post by currentshaft on 2024-08-09
.

---

### Post by cigtoxdoc on 2024-08-09
Bootable USB made as usual with Startup disk creator.  Did not try to use USB as nothing in BIOS settings would permit use of a USB stick.

---

### Post by currentshaft on 2024-08-09
.

---

### Post by cigtoxdoc on 2024-08-10
Thank you, but Lenovo BIOS, does not let you set boot order to USB stick.  Choices are USB HDD, USB CDROM, and SATA4: PLDS DVD-RW DA8A.  There is a DVD drive built into the PC, so I suppose that I could burn a bootable DVD disk.  However, one would think that there is a easier way/  John

---

### Post by tea for one on 2024-08-10
> **cigtoxdoc said:**
> Thank you, but Lenovo BIOS, does not let you set boot order to USB stick.  Choices are USB HDD
Of course, Lenovo lets you boot from USB

Power off the PC
Attach prepared bootable USB
Power on and press dedicated key F12

Boot menu
1. Ubuntu
2. USB HDD: Sanddisk Ultra  (This is a USB thumb drive)

Arrow down to 2
Hit Enter

---

### Post by currentshaft on 2024-08-10
.

---

### Post by cigtoxdoc on 2024-08-10
Thank you for your suggestions.  Followed what tea for one wrote.  It did not work at first with the USB stick in a "SS USB" port. It went right to Win 11.  I tried again with the USB stick in a "10 USB" port and it worked.  

John

---

