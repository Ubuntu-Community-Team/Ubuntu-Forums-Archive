---
title: "Error messages on attempted install"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by carnetarian on 2008-07-26
I'm trying to get my brand new computer to dual boot between the 64 bit version of Ubuntu 8.04 and Vista 64. Vista has been working solidly for a day now and has had no problems whatsoever. However, when I try to install Ubuntu or check the live cd for errors it puts out error messages like
"Buffer I/O error on device fd0, logical block 0"
for about 15 minutes, then the screen just goes blank. 

I ran the memory test on the Ubuntu cd and everything checked out.
I put the cd in my old computer and tested it for errors there and it worked fine.

I'm not sure if it's relevant, but here's the build of my new computer:
ASUS P5Q Pro LGA 775 Intel P45 ATX Intel Motherboard
Intel Core 2 Duo E8400 Wolfdale 3.0GHz
Patriot Extreme Performance 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
Western Digital Caviar SE16 WD6400AAKS 640GB 7200 RPM SATA 3.0Gb/s Hard Drive
MSI R4850-T2D512 Radeon HD 4850 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Video Card
SAMSUNG 22X DVD Burner Black SATA Model SH-S223F

Thanks in advance for any help.

---

### Post by Partyboi2 on 2008-07-26
try going into the bios and disabling the floppy if you have one.
Another option you could try is to use a boot option like
```
nofloppy
``` or ```
all_generic_ide
```
You can add this by pressing F6 at the main menu and adding it to the end

---

### Post by carnetarian on 2008-07-27
Thanks! The first two recommendations didn't work, but the third one did.

---

