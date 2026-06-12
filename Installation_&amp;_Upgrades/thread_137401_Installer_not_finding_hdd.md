---
title: "Installer not finding hdd?"
date: 2006-02-27
forum: Installation &amp; Upgrades
---

### Post by negatiiv on 2006-02-27
Hello all,

What I want to do: I am attempting to install Ubuntu 5.10 on a hard disk so that I can boot from either Ubuntu or Windows XP. My Windows install is on one hard drive, and I am trying to install Ubuntu onto the second hard drive. I left some space on the second drive unpartitioned so that Ubuntu can do with it as it pleases.

My problem: When running the installation from the CD I have, I get to the section about adding/resizing partitions. I am able to see options pertaining to one of the hard disks, of which I have windows installed on already. However, I do not see any mention of my second hard disk or the free space on there I want to use. Is it possible that the install-cd is not recognising either my second hard drive or the controller it is attached to? Any other ideas? P.S. Windows XP is able to see and use both of the hard drives without a problem, so I believe the hardware is set up correctly.

For reference, as it might be important, here is what I have set up for hardware:

AMD Athlon64 X2 4200+

2gb (2x 1024mb) PC3200 Ram

Asus A8N32-SLI Motherboard (note, has both:
   -'Nvidia Nforce 4 Serial ATA Controller'
   -'Silicone Image SiI 3132 SATALink Controller')

2 hard drives:
   -Western Digital 74GB attached to nvidia controller (contains 1 ntfs partition with windows installation)
   -Western Digital 250GB attached to Si controller (contains 1 210GB nfts partition, and ~30GB unpartitioned space)

eVGA 6800GS 256mb pci-e video card


Thank You in advance for the help!

---

### Post by mr_mop on 2006-02-28
Can you try putting them on the same controller? If the kernel doesn't support the SI controller, then it wont be able to see it.

---

### Post by negatiiv on 2006-02-28
I was hoping not to put them on the same controller. I was told that by using separate controllers I would get a performance increase when using both drives at the same time.

---

