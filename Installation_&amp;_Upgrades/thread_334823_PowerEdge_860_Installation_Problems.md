---
title: "PowerEdge 860 Installation Problems"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by smaw0351 on 2007-01-09
I am trying to install Ubuntu 6.06 Server on a poweredge 860 (below are the configurations). I am using a hardware RAID1. The installation hangs when it tries to read the disks / partitions.  I'm running the installation disk off of a usb cdrom. Dell offers NO support for Ubuntu!! I have researched everywhere and havent found the solution yet. Any advice would be greatly appreciated.

1 222-6547 915, 2x2MB Cache, 2.8GHz Pentium D, 800MHz Front Side Bus for PowerEdge 860 
  1 311-5214 2GB DDR2, 533MHZ, 2x1G, Dual Ranked DIMMs, PowerEdge 8X0 
  1 430-1765 Broadcom TCP/IP Offload EngineNot Enabled 
  1 320-4959 Riser with 2 Slots: 1 PCI Exprx8 slot and 1 PCI Express x4 slot 
  1 341-3803 250GB, SATA, 3.5-inch 7.2K RPMHard Drive 
  1 341-3874 SAS5iR SAS RAID Controller, Internal, PCIe 
  1 420-6320 No Operating System 
  1 430-2008 On-Board Dual Gigabit Network Adapter, No TOE 
  1 320-2961 NO CD-ROM OPTION 
  1 313-4428 Bezel 
  1 310-8180 No Hard Copy Documentation E-Docs Only and OpenManage CD Kit 
  1 341-3803 250GB, SATA, 3.5-inch 7.2K RPMHard Drive 
  1 341-3870 Add-in SAS5iR RAID Controller (SATA/SAS Controller) which supports 2 Hard Drives - RAID 1 
  1 310-6711 No Rails Included for PowerEdge 850 
  1 985-1267 Dell Hardware Warranty Plus Onsite Service Initial Year 
  1 970-0940 Basic Enterprise Support: Business Hours (5X10) Next Business Day Onsite Service After Problem Diagnosis Initial Year 
  1 985-1378 Dell Hardware Warranty, Extended Year 
  1 960-5302 Basic Enterprise Support: Business Hours (5X10) Next Business Day Onsite Service After Problem Diagnosis 2 Year Extended 
  1 985-1317 BASIC Enterprise Support:Business Hour (5x10) Hardware-Only Technical Phone Support, 3 Year, Declined Software Support 
  1 900-9997 On-Site Installation Declined

---

### Post by samroy on 2007-11-12
Hi there,

No I don't have the solution but I do have the same problem!

Have you managed to install it? Let me know if you're actually running ubuntu on your PE860 machine!
Thanks!

---

### Post by Technophobia on 2008-01-29
So you were able to boot the CD at least? When I try to boot a Ubuntu Server CD if show the first screen and then locks up. I can boot a windows2003 cd and the Dell support OS install CD, but sadly not Ubuntu Server.

---

### Post by bytemind on 2008-04-01
Update...

Did you get it installed, maybe the 7.10 server version?

---

### Post by Technophobia on 2008-07-22
Works for me now! 


I was just looking around the bios and decided to change under "Integrated Devices" - SATA Controller = ATA MODE and USB Controller = On with bios support.

3 out of 9 servers at my work now run Linux. Not counting NAS (terastation)

---

