---
title: "problem with HDD installation"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Trojan92 on 2010-02-23
Hello to all, 
I bought a new brand Toshiba Satellite p300 series at the end of 2009 and i used it for just few weeks and then the hard drive crashed...It's beyond repair now but i've gotten a new hard drive already, which when i try to install and operating system, it tells me my machine cannot access the drive but yet i'm seeing the drive in the BIOS. Can someone please help me with further solution?

---

### Post by darkod on 2010-02-23
Can you boot with ubuntu cd, Try Ubuntu option into the live desktop? If yes, open Gparted in System-Administration and check if it can see the hdd.
Also in terminal run:

sudo fdisk -l

to see the partitions/hdd. It might be just that it wants to write a partition table because it's brand new, although it shouldn't refuse to install an OS just because of that, it will write the partition table during install.

---

