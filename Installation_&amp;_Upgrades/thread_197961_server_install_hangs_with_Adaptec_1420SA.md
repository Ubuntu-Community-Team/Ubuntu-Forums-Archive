---
title: "server install hangs with Adaptec 1420SA"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by lackhead on 2006-06-16
Hey all-

I'm trying to install 6.06 server on a dual-core opteron system (using the server AMD64 disk). The system disks are two Seagate drives hanging off of an Adaptec 1420SA. When the install fires up, it runs smoothly until I get to when partman fires up and then the machine just goes off to la-la land.  The keyboard is still reponsive and the machine isn't *hung*, but it never moves forward (I am left with a blue screen of death, funnily enough). 

I have tried this with the disks in RAID-1 and JBOD mode with the same results.  I have also tried installing using the desktop disk, which manages to get on to the disk partitioning screen, but will only see the two separate disks and not any RAID group (this I can get around by installing on one disk in JBOD mode and then setting up the mirror, initializing from the installed-to disk). 

Anyway, I would much rather install from the server disk than the desktop (I have scripts that assume a server build), so does anybody have an idea about how I can get this card to work with 6.06? 


Thanks!


-c

---

### Post by pigor on 2006-08-30
The Adaptec 1420SA card has a software RAID and it needs driver. I've been trying to recompile the source code they put on their website but I haven't past through the errors so far. Anyway, even if Adaptec had released the driver for Ubuntu/Debian it wouldn't work straight off the install CDs.

---

