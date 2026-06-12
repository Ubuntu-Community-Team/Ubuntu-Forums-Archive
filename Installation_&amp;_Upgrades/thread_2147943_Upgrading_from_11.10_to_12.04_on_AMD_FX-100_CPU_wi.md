---
title: "Upgrading from 11.10 to 12.04 on AMD FX-100 CPU with nVidia"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by juanbuntu on 2013-05-23
Dear Folks


Last year I tried to install Ubuntu 12.04 on my machine but it failed pretty badly, to the point that I had to install 10.04, and from there upgrade to 11.10, which is what I am currently running. I am getting messages inviting me to upgrade to 12.04 LTS, but the experience I had last year was so bad that I have not done so. 

My system configuration is as follows:


CPU: AMD FX-6100 Zambezi 3.3GHz Socket AM3+ 95W Six-Core Desktop Processor
MOBO: ASUS M5A97 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS Version = 1208
Video Card: EVGA 01G-P3-1556-KR GeForce GTX 550 Ti (Fermi) FPB 1GB 192-bit GDDR5 PCI Express 2.0 x16 HDCP Ready SLI Support 
Memory: CORSAIR Vengeance 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) 
HardDisk: Western Digital Caviar Blue WD10EALX 1TB 7200 RPM SATA 6.0Gb/s 3.5"
DVD: ASUS DRW-24B1ST/BLK/B/AS Black SATA 24X DVD Burner 


So here is the question: Has 12.04 been tested and known to upgrade OK on systems such as mine with AMD multi-core CPUs with GeForce GTX cards, which is nVidia?


Many thanks

---

### Post by 2F4U on 2013-05-23
It would be helpful if you could describe the problems you had the last time you tried to upgrade to 12.04. To get a pretty good impression on how 12.04 runs on your hardware, you should first run a live system.

---

### Post by juanbuntu on 2013-05-23
[COLOR=#000000][INDENT]In May 2012 I installed Ubuntu 10.10. in Early June I upgraded to 11.04, in mid-June upgraded to 11.10. Then I tried to upgrade from 11.10 to 12.04, but the upgrade process had numerous error messages.
So I had to recreated the install/update sequence starting from 10.10->11.10 and did not have the courage to go to 12.04.

Is there a compatibility problem caused by having an nVidia GeForce graphics card with an AMD CPU?
[/INDENT]
[/COLOR]

---

### Post by juanbuntu on 2013-05-23
> **2F4U said:**
> It would be helpful if you could describe the problems you had the last time you tried to upgrade to 12.04. To get a pretty good impression on how 12.04 runs on your hardware, you should first run a live system.

[COLOR=#000000]In May 2012 I installed Ubuntu 10.10. in Early June I upgraded to 11.04, in mid-June upgraded to 11.10. Then I tried to upgrade from 11.10 to 12.04, but the upgrade process had numerous error messages.[/COLOR]
[COLOR=#000000]So I had to recreated the install/update sequence starting from 10.10->11.10 and did not have the courage to go to 12.04.[/COLOR]

[COLOR=#000000]Is there a compatibility problem caused by having an nVidia GeForce graphics card with an AMD CPU?[/COLOR]

---

### Post by juanbuntu on 2013-05-23
I burned the AMD64 version of the 12.04.2 .ISO image and booted the live system directly from the DVD. Everything seems to be running just fine. The live system even recognizes the partitions and the devices (disks, video cards, nic, mouse, KB, etc).

QUESTION: In your experience, is having the live system running from the DVD a 'good enough' test?
Would you recommend that I take the plunge and upgrade to 12.04.2 from 11.10?

Thanks
juanbuntu

---

