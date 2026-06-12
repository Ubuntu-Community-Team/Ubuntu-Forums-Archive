---
title: "Problem booting from SATA"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by pjbgravely on 2007-10-06
I have a (new to me) but older HP P4 MB, that I wanted use. I bought a SATA PCI card, 2-320GB drives, and some memory and installed 7.04.

   I discovered that the MB would not see the SATA card as a boot device, so I put in a 40 GB IDE drive and moved /boot to there. After that didn't work I reinstalled Ubuntu with the new setup.

   Now there seems to be some timing problem, I can boot, but even in rescue mode, all the partitions are read only. GDM fails with a permission problem and I cannot write to any partition even as root. Mount says all three partitions are mounted r/w with the loop backs. I have hdc1 ext3 as /boot, sda1  reiserfs as /, and sda3 reiserfs as /home. 
I checked dmesg, ( I can't post it because I can't write) and it was complete with no errors. The logs are empty so the kernel couldn't write to the drives either. 

    If anyone has a clue about what error log might tell me where the problem is I will be able to go on from there. If not then I will try and install / to hdc, this will run slower, so I am trying to avoid it.

Paul

---

