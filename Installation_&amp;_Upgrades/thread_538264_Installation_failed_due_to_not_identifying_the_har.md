---
title: "Installation failed due to not identifying the hard disk (PC Asus, Promise)"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Ganton on 2007-08-29
**PROBLEM:**
- The Ubuntu 7.0.4 installer does not identify my hard disk. Probably due to drivers of "Promise Mass storage controller PDC20265" and Motherboard Asus "A7V".

**RELATED INFORMATION:**
- Trying to install OpenSuse 10.2 at first it didn't detect my hard disk but it said when loading that you can try the boot parameter "brokenmodules" and so I used 
	brokenmodules=pcd202xx_old
and it said it was loading the "pata_pcd202xx_old" module and it installed correctly.

- The hard disk is correctly detected by Knoppix 4.0.2 but not with Knoppix 5.1.1 (which makes me think of kernel modules).

- I have checked the health of the harddisk.  The health of the hard disk is good, in fact I'm writing this  booting from another partition of this hard disk (with Windows). I have there installed now also the OpenSuse Linux, so I can perform any tryings you need.

- I've checked the md5sum of the Ubuntu install disk, and it showed to be ok. 

**QUESTION:**
- For installing Ubuntu in the computers with this hardware:
is there something similar for Ubuntu in order to load a module or not-to-load one? How can be installed?

---

### Post by Ganton on 2007-08-29
Result of lsmod

---

### Post by Ganton on 2007-08-29
Result of lshw

---

### Post by Ganton on 2007-08-29
Result of lspci -vv

---

### Post by Ganton on 2007-08-29
Result of cat /proc/partitions      (is correct)

---

### Post by Ganton on 2007-08-29
In OpenSuse, result of cat /proc/partitions  (is correct, too)

---

### Post by Ganton on 2007-08-29
In OpenSuse, the result of   fdisk -l   (it is correct). In Ubuntu executing fdisk -l only shows errors. The disk is in a correct state, I can see its content amd test it from Knoppix and Windows.    

fdisk shows errors because it can not detect the disk.

---

### Post by Ganton on 2007-08-29
In OpenSuse, result of lsmod

---

### Post by Ganton on 2007-08-29
In OpenSuse, result of lspci -vv

---

### Post by Ganton on 2007-08-29
In OpenSuse, result of dmesg

---

### Post by Ganton on 2008-07-09
I tried with Ubuntu 7.10 and failed the same way, but in Ubuntu 8.04 worked!

My congratulations to kernel developers, Ubuntu developers or whoever it was, the hard disk wasn't identified since Ubuntu 4.10.

---

