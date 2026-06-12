---
title: "Only Lubuntu 12.04 can install on i5-3450 Ivy bridge system"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2012-10-22
I have been trying to use a ?ubuntu operating system on a Jetway NF9E-Q77 motherboard with i5-3450s Ivy-Bridge CPU, 4G ram and no OCZ agility SSD. The SSD broke and until I get a replacement I cannot install permanently. I am just trying to run from a USB memory stick.

 Results:

Ubuntu 12.04 - total failure, huge number of error messages. Boot hangs.

Lubuntu 12.04 - Installs and seems to work pretty well (apart from file manager).

Ubuntu 12.10 - total failure. Boot hangs.

Lubuntu 12.10 - total failure. Boot hangs.

I have tested the memory sticks on another machine and they boot perfectly, so I am sure it is not a problem with the download or bootable USB creation.

I would like to give more details but I don't know how to get the massive number of error messages off a crashed machine.  There are many kernel panics booting Ubuntu 12.04.  Lubuntu 12.10 complains that user Lubuntu already exists and that it cannot mount directories.

I feel there must be a clue from Lubuntu 12.04 working.

I have never used linux in any serious way so my knowledge is pretty basic.  I would appreciate any ideas on how to get Lubuntu 12.10 going, since I think this may solve the file manager problems that I had in 12.04

---

### Post by elpidiovaldez5 on 2013-02-13
In case anybody else has trouble installing Lubuntu on Jetway NF9E-Q77 motherboard, I finally found a partial solution:

Use the 'noapic' option in the boot command.  This allows all the kernels that I have tried to work with Lubuntu 12.04 including PAE kernels.

I still cannot boot Lubuntu 12.10 or any version of Ubuntu on this board.

---

