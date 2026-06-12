---
title: "Grub install fails   . What to do ?"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by iansen on 2008-02-12
Here is the problem : 
 
I'm trying a dual boot on my laptop  Ubuntu 7.10 / Vista Home Premium - using the steps described [here ]("http://neosmart.net/wiki/display/EBCD/Ubuntu") 

Except I made the partitions logical .... because  I already have 3 primary partitions on my computer(first partition is hidden - laptop backup or something, the second has Vista on it) ... I tried primary partitions first but I could only create 1 - swap or / .

Everything goes well until the install process reaches 95% .... installing grub .... after a few seconds I get a fatal error Grub Install Failed  on hd  0, 6  ... this is a fatal error and the installer stops.

What can I do to get it past the grub install ? Am I missing something ? :confused:

Thanks

---

### Post by housam on 2008-02-12
No problem changing one of the primary partitions to an extended one which can be devided to many logical partitions . you can install Gutsy on a logical partitions ( I did that on my laptop ) but with regard to the size of the partitions ( at least 10 Gb for the root (/) and 1 GB for the swap).
Start it all over again, Create your partitions manually using Gparted tool and choose the manual sellection during the installation.

---

