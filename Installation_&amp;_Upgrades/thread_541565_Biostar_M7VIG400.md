---
title: "Biostar M7VIG400"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by billmoss on 2007-09-03
I tried to install 7.04 on a Biostar M7VIG400. The GUI installation crashes and put me into a shell prompt. I installed all the drivers I could find on Via Web site for Ubuntu and installed using the driver CD; same result.

OpenSuSE 10.2 and Fedora core 7 both run on the machine.
I tried the installation with the configuration I use to run Fedora, 2 GB of RAM, ATI 72xx AGP and Athlon XP 1.8 GHz. I also tried using the system board's graphics with the same results.

I am not new to Unix/Linux (I still have my 1978 Lab Version 7 manuals) but the error messages during the failed install are not particularly informative. My guess is a BIOS incompatibility and/or I/O subsystem problem.

The system runs on a Vanilla ATA/100 Seagate 160 GB drive. CD is a Sony DRU-830.

I tried booting on a working 7.04 system (from a different machine) and this fails on the GDM load and puts me at a command prompt (appears to be run level 3).

None of the system probe tools I am familiar with are available, so figuring out what is not happening is a pain. Walking the /proc file system is no longer my idea of fun.

dmesg and /var/log/messages also show nothing  of interest, just that GDM and the X server failed. I don't know if this is the related to the installation failure or just another incompatibility.

Note, I do have 7.04 running on an old Iwill XA100+ system board which is the drive I used to test the M7VIG400.

---

