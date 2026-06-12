---
title: "Canon ImageClass D460-490 Driver Install"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by tactac on 2011-03-22
In order to use the system-config-printer tool (menu System > Administration > Printing)  to install my Canon driver on Karmic and Lucid I followed a lead from a similar launchpad thread:

(1) Go to [http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)
(2) Twiddle the selectors until you find and download UFR_II_Printer_Driver_for_Linux_V220_uk_EN.tar.gz
      (Note the version VXXX may have changed)
(3) tar -xzf UFR_II_Printer_Driver_for_Linux_V220_uk_EN.tar.gz
(4) Find the appropriate .deb file in there per your OS flavor
(5) sudo dpkg -i cndrvcups-ufr2-uk_2.20-1_i386.deb cndrvcups-common_2.20-1_i386.deb
(6) follow through the normal new printer install dialog. for me in both cases it found the right driver.
(7) print

---

### Post by jfl on 2011-05-23
A big Thank you !!!

I had a Canon ImageClass D-480 and had to revert to Windoze (or VB) to print on it.

Followed your instructions, worked the first time !!!

Using Maverick 10.10 :D

---

