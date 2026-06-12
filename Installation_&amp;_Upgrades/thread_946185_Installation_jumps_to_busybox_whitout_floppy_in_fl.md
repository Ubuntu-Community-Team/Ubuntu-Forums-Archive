---
title: "Installation jumps to busybox whitout floppy in floppydirve and finds no harddrives"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by christian.adeen on 2008-10-13
I can't get the installer running whitout a floppydisk in my floppydrive. Whitout one it craches to busybox. Whit one in the drive, the installer wount find my hardrive.

All my hradware is working, I've tried whit differnt biossettings like running in native IDE mode or AHCI no change. 

I have slamd64 12.1 installed and it is working fine. 

PS. I inserted the floppy after chosing "install kubuntu kde4" and when I get this error:

<some large integer here> Buffer I/O error on device fd0, logical block 380

I force the floppy out. And installation starts. 

I have 4 partitions on my HDD,
1st is swap
2: my slamd64 system
3: emty ( for kubuntu )
4: /home for slamd64 and hopefully for kubuntu)

My boot loader is Lilo and it's installed in the MBR

This is my computers specs:

Motherboard, ECS KA3 MVP REV 1.0A
Memory: 2x2gb of DDR2 800mhz in dual chanel mode from Mushkin
Processor: AMD Athlon64 x2 5200+ (AM2)Harddrive Samsung SP2504C SATA2 250gb on IDE Channel 2 (SATA) ACHI
HL-DT-STDVD-ROM G master on IDE channel 0 (PATA)
_NEC DVD_RW ND-35 Slave on IDE channel 0 (PATA)
NVIDIA geforce 8500gt 256mb from gainward (PCI-e)

---

