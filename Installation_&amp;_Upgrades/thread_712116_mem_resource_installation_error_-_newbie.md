---
title: "mem resource installation error - newbie"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by tarzan2001 on 2008-03-01
Hi.  I'm trying to install Ubuntu for the first time.  I've tried using both the 32- and 64-bit versions of Ubuntu 6.06.1 LTS.  I'm getting an error that apparently other users have experienced before, however their systems still booted fine, and usually this was occurring on laptops.  My problem happens on my desktop when I choose "Start or Install...".  It gives the following error after loading drivers ok:



Uncompressing Linux... Ok, booting the kernel.
[17179570.124000] PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0



This ends at some type of command prompt.  After this it doesn't proceed at all.  The specs for my system are as follows:

Processor: Intel Core 2 Duo E6600 (2.4 GHz)
Motherboard: Intel DG965RYCK
RAM: 2 GB DDR2 667
Graphics card: NVIDIA GeForce 8600 GTS 256 MB DDR3
Harddrive: 160 GB SATA

I don't know if this is due to some error with the graphics card.  I tried the "graphics safe mode" also, but to no avail.  Kept getting the same error.  I also tried adding the "live apci=off" command to the boot options, but that didn't help either.  Does anyone have any suggestions?  Any help is greatly appreciate because I really want to try out this OS. :D  Thanks!

---

### Post by Pumalite on 2008-03-01
Install with the Alternate CD.

---

### Post by tarzan2001 on 2008-03-04
Yeah, I did try to use the other CD, but it didn't work either. :(

---

### Post by Pumalite on 2008-03-04
Clean the lens in your bgurner. Try the CD's in a different computer.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less as image, not 'data', in good quality CD-R media, check CD integrity before install.

---

