---
title: "Hardware recommendations"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by kevinfreitas on 2006-08-14
Just bought the following hardware config and cannot get Ubuntu to run as smoothly "out of the box" as with other PCs around the house:

- ASUS P5RD2-VM Socket LGA 775 ATI Radeon XPRESS 200 Micro-ATX Motherboard
- Intel Pentium 4 630 Prescott 800MHz FSB LGA 775
- CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 675 (PC2 5400)
- 2 Seagate Barracuda 7200.9 ST3808110AS 80GB 7200 RPM SATA 3.0Gb/s Hard Drives

I thought this would be a screaming server that I could setup RAID but am really down on the whole thing at the moment. This is the first time I'm building a new server without the old one having crashed.

Any help would be incredibly appreciated -- I'm trying to figure things out quickly in case I need to RMA any of the parts.

Thanks!   ~ Kevin

---

### Post by nalmeth on 2006-08-14
> Just bought the following hardware config and cannot get Ubuntu to run as smoothly "out of the box" as with other PCs around the house
Whats not running properly? Hardware problems? Network or graphical problems?

---

### Post by kevinfreitas on 2006-08-14
I'm not 100% sure but everything I've been able to track down points to the mobo chipset being too new. The install process halts nearly right after beginning on a "Kernel panic - not syncing: Attempted ot kill init!" message.

I've referred to another guys site (at [http://laddie.wordpress.com](http://laddie.wordpress.com)) with the same mobo and he had a line something like "boot: live pci=noacpi ide=nodma ide=reverse" that he said worked but did me no good.

Thanks for the help -- I so want this to work it's not even funny.

---

