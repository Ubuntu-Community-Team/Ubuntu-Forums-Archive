---
title: "Ubuntu 10.10 fails to install from CD, USB &amp; virtual dektop on Acer Extensa 5235"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by T-M-H on 2010-11-10
Right after selecting [Install Ububtu] / [Try live CD], I get this message and the system freezes. The same message appears when trying to install Ubuntu from VMWare Player or booting from a CD instead of a USB stick. Has anyone else experienced the same?

[IMG]http://i33.photobucket.com/albums/d100/deliriumus/IMG_7933.png[/IMG]


Processor :    Intel Celeron 900
Mainboard :    Acer BA50-MV
Bios : Phoenix  V1.3311
Chipset :    Intel GL40
Video Card :    Mobile Intel(R) 4 Series Express Chipset Family
Hard Disk :    Western Digital WD1600BEVT-22ZCT0 ATA Device (160GB)

My old HP Pavilion boots and installs Ubuntu 10.10 just fine from the same USB stick. I have tried both 32bit and 64bit editions with same results.

---

### Post by sikander3786 on 2010-11-10
Try adding some boot parameters like acpi=off and noapic. There are 6 of them. Try them all.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

