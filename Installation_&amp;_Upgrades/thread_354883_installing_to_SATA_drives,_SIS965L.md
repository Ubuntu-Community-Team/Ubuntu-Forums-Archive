---
title: "installing to SATA drives, SIS965L"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Packman5280 on 2007-02-06
I need some help getting Ubuntu installed onto my roommates PC that we just built.  Here are some specs

AMD Athlon 2800+
SiS 965L chipset, PCchips Mobo
512MB RAM
2 160GB SATA drives

Here is the problem, gparted fails when it asks me to partition the drives, telling me there are no devices detected.  The drives are visible to the BIOS.  I tried only using one drive, changing the mode in the BIOS to IDE, the drives are not visible at all.

I understand that the SiS chipset we are using does not have a driver in the 2.6.18 kernel, but SiS makes a driver for kernel 2.6.10 which i have downloaded to USB key.  They also have a 2.6.9 kernel driver, but I figured the earlier one would be best.  If that is wrong let me know.

So I need to figure out how to load the SATA drivers when booting from a live CD, so that the installer can see the drives, partition them, and install the OS, but I have no idea how to install a driver when I can't see the hard drive.

Any help is much appreciated.

---

### Post by roofchop on 2007-02-06
I am new at this, but thought I could add some input.  I installed Ubuntu 6.10 for the first time yesterday and it had no problems finding and partitioning my SATA drive.  My problems came after the installation.

---

### Post by Packman5280 on 2007-02-06
my system has an nVidia chipset, which is supported, and sees the drives fine (except for RAID, which I have found a how to for).  it's just his SiS chipset that does not have a SATA driver built into the default ubuntu kernel where I am having the problem.

---

### Post by confused57 on 2007-02-06
I don't have a solution, but I haven't had any problems installing any Linux distro on my Abit mobo with chipset SIS 661FX/964(L), which is probably older than the SIS965L...maybe you could try Feisty to see if the newer kernel contains the needed driver, Sabayon might be a distro that you could "test" if it'll recognize the hard drives.
I have both a IDE and SATA drive & no problems with either...sorry I can't help, but thought I'd mention my experience with SIS964L...good luck.

---

### Post by Packman5280 on 2007-02-08
well, no other distros seem to be able to see it either.  fedora, suse, can't see the controller at all.  oh well, just got an ide drive to put the OS on.

---

