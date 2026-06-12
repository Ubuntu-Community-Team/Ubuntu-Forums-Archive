---
title: "Alternate Install CD RAID Drivers"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by igul222 on 2006-08-17
I have been using Ubuntu for a month or two now, and just got a new HDD, and set it up with my old one in a RAID-0 array. My ITE8212 controller apparently isn't supported by the dapper alternative CD (or the edgy one, for that matter). My motherboard manufacturer provided me with driver binaries and source code for this controller, and it seems that you can load drivers from floppy with the alt. install disk. How do i load the drivers, and what files do i need to copy? (I have a .o file, a Makefile, and a .c file) Please help me get this thing to work!

---

### Post by gerbman on 2006-08-21
You probably need to compile the drivers first. What files did you download for the driver?

---

### Post by igul222 on 2006-08-22
there was a .h file, a .c file, and a .o file. you can download the package here. this was the only download i could find, and it comes bundled with windows drivers.

[ftp://dlsvr01.asus.com/pub/ASUS/misc/ide/ite8212/ITE8212.zip](ftp://dlsvr01.asus.com/pub/ASUS/misc/ide/ite8212/ITE8212.zip)

---

