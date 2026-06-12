---
title: "install ubuntu in unpartisan area"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by ramakanta on 2012-02-20
I have windows7 OS. and also 60 GB unpartisan of harddisk.
please help me with detail procedure of installation of ubuntu 10.10 in partitions  area of hardisk .
thank you.

:confused:

---

### Post by Frogs Hair on 2012-02-20
Hello and Welcome 

10.10 will reach end of life and loose support in April . If you want to install now consider 10.04 or 11.10 because either will allow the upgrade to 12.04 due for release in April, which will have support for 5 years .

Beyond the information at the link a search will provide plenty of dual boot information and even videos . Make sure that any information you find is current to the Ubuntu version you wish to install . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by ramakanta on 2012-02-21
> **Frogs Hair said:**
> Hello and Welcome 

10.10 will reach end of life and loose support in April . If you want to install now consider 10.04 or 11.10 because either will allow the upgrade to 12.04 due for release in April, which will have support for 5 years .

Beyond the information at the link a search will provide plenty of dual boot information and even videos . Make sure that any information you find is current to the Ubuntu version you wish to install . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
thanks for this link..

Now  i had download the 11.10 version. please tell me the procedure.of installing ubuntu in un-partitions area . is it same or different.

thank you

---

### Post by Mark Phelps on 2012-02-23
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

