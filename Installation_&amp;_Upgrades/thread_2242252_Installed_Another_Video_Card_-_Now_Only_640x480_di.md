---
title: "Installed Another Video Card - Now Only 640x480 display"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2014-08-31
System: Dell Precision 390, 1GB Ram, 250GB SATA
OS: UbuntuStudio v14.04

Installed Another Video Card (XFX ONE 1GB DDR3 PCIe16) - Now Only 640x480 display, and it won't let me change it. Am I stuck with this display? Help please! 

On the box it says it is a ATI Radeon HD 5450, and supports Linux and FreeBSD. 

Any suggestions?

Thanks!
Rick

---

### Post by QIII on 2014-08-31
Hello!

Did you previously have a different card or brand with a proprietary driver installed?

---

### Post by Rick St. George on 2014-08-31
Yes, it was what came with the Precision 390 - Nvidia Quadro NVS285 128Mb DDR2 SDRAM PCIe16 w/DMS-59 output port. Part No. 180-10383-0000-A01

Don't know about the Driver, v14.04 installed whatever it did upon installing the OS.

Wanted to give this old system new life, as it has a dual core processor and should perform well with Ubuntu.

---

### Post by Rick St. George on 2014-08-31
Sorry ... Apparently I needed to Enable the "FGLRX" (proprietary) driver instead of the default Xorg Xserver driver (open source - tested), then of course - REBOOT. Then the screen was resized automatically, and also Catalyst shows up in SETTINGS in order to customize. Next I will try to add another monitor and see if it will recognize and display both properly. 

Thanks!

---

