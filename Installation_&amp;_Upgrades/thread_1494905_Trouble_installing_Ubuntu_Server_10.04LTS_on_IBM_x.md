---
title: "Trouble installing Ubuntu Server 10.04LTS on IBM x3650 server"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by smipi1 on 2010-05-27
I am having trouble installing Ubuntu Server 10.04LTS on an IBM x3650 server (Model 7945 K2G).  The install CD cannot find the drives, so I cannot continue with the installation.  Manually selecting mptsas as the storage driver doesn't work either.

I have tried various permutations:
1. 64 / 32 bit Ubuntu Server
2. Using weBIOS to configure a RAID0 redundant virtual drive or not
3. Loading BIOS defaults or messing with most of the related settings

This particular server makes use of the ServeRAID M1015 controller (based on an LSI SAS2008 device).

Has anybody got this working?
Can anybody assist?

---

### Post by jpbrnz on 2010-05-27
I ran into the same problem a few weeks ago.  I was not burning the CD image correctly when I was receiving this message.

Check this out [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope it helps.

---

### Post by smipi1 on 2010-05-28
The CD has been written correctly.  Checking the CD image in the installer start page confirmed this.

---

### Post by amtzone on 2010-12-13
hello mate.....did u found the solution??
i also encounter the same problem here....still cannot be solved...i also did all the same as u did....still cannot install the OS....

---

### Post by smipi1 on 2010-12-13
I gave up and installed VMWare ESXi.  Now running a few instances of 10.04LTS as virtual appliances.  I needed to cover the use-cases ASAP, and this solution works quite well.  Besides... neither IBM nor the Ubuntu forum seemed to care about getting Ubuntu 10.04LTS working on the hardware.

At least IBM officially supports VMWare ESXi, so that part of it ran without a hitch.  Besides... VMWare ESXi is free(-ish).

---

### Post by amtzone on 2010-12-15
ubuntu 10.10 seems to be working...the problems is i have to use 10.04 no matter what....

---

