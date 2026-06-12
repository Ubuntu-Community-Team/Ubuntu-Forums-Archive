---
title: "Installation help - Ubuntu on Intel DG33TL,  Core 2 Quad Pro Q6600"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by nishchals on 2007-10-06
I am new to linux and just tried my hands on a newly built system (everything from scratch). Right now, I am stuck with infamous "Cant access open tty" issue of Ubuntu 7.04 - i read about this a lot on forums. However, i have many questions before even i jump to try resolving this issue. It will be great if someone can help me jump start me on Ubuntu with questions below.

If someone has installed Ubuntu on newly built systems, let me know. 

My HW is 
       Intel Core 2 Quad Pro Q6600/DG33TL Motherboard
       One HP 300N DVD writer on IDE (master), looks working fine.
       One 250GB SATA HDD connected to SATA01 port and BIOS configures as "Configure SATA as IDE". Other options were RAID and AHCI, which i dont think i should have selected, correct me if wrong. 
       No floppy drives


I see following problem - HDD is detected by BIOS and displays capacity, but no other boot is able to recognize this as a volume after the boot. (DOS boot/XP installation/also Ubuntu possibly causing the error above). For DOS/XP 0 i can understand - i did not install the ATAPI driver from Intel box which is on a floppy. (Its kind o strange as motherboard has no floppy ports)

However, with ubuntu, 
   1 - do i need to go for option which says "Install with driver setup"? Is the default packaging includes driver for IDE controller for what is required for Intel DG33TL.  
   2 - if not, where can i find DG33TL IDE / RAID controller drivers to use with Ubuntu installation? Whats i find on the net is all for windows XP vista
   3 - Shall i try other linux packages (fedora/gnome), will that help?
   4 - Is my SATA configuration OK?
   5 - HDD is brand new from factory - will formatting this externally and then installing it help?

---

