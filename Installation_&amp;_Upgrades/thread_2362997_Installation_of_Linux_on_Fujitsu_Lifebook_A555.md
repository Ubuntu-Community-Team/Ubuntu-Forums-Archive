---
title: "Installation of Linux on Fujitsu Lifebook A555"
date: 2017-06-05
forum: Installation &amp; Upgrades
---

### Post by ankur881120 on 2017-06-05
Hi Experts,

I want to understand that whether or not I can install Linux on

"Fujitsu  Lifebook A555 - Core i3-5th Gen/ 8GB RAM/ 1TB HDD/ DVD-RW/ 15.6"/ DOS".  Also, will there be any sort of problems after installation, like  internet connectivity, bluetooth connectivity, program execution, java  issues etc.

Here are the specifications:
Processor Brand	Intel
Processor Type	Core i3
Processor Speed	2 GHz
Processor Count	1
RAM Size	8 GB
Computer Memory Type	DDR3 SDRAM
Hard Drive Size	1 TB
Hard Disk Technology	HDD
Hard Drive Interface	Serial ATA
Hardware Platform	DOS
Operating System	DOS

The graphics card configuration: Intel® HD Graphics 5500

---

### Post by howefield on 2017-06-05
Looking at the specifications it would seem likely that the machine will run Ubuntu well enough, but it is easy enough to test what works out of the box with a Live USB stick.

---

### Post by oldfred on 2017-06-05
Is it similar to any of these older models?
 Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442) 

If you have DOS, is system actually UEFI or BIOS based. 
Most new hardware is now UEFI.
But if DOS then partitions would be MBR(msdos) which is usually BIOS.

---

