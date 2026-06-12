---
title: "No CD-Rom Detected"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by bc_320 on 2009-12-15
I decided to give Xubuntu a try.  I have an old machine (specs follow).  I have been trying to install it but keep running into a problem.  When the process gets to detecting cd-rom I get the following message: "No common CD-ROM drive was detected".  I have tried all the  options under the F6 menu that are available at the first screen.  I found a thread that had me type "modprobe ide-scsi" but that did not do anything.  I can't figure out what CD-Rom I have.  I also have no internet access on this machine.   I cannot install from anything else but the CD-ROM.

Ideas?

specs:
-Microprocessor 366 MHz AMD-K6-2 processor with 3DNow! technology 
 -Microprocessor Cache 512 KB L2 Pipeline Burst Cache 
-Memory     64 MB SyncDRAM (US)  
-Video Graphics          * High-performance 3D graphics     
-Maximum internal resolution of up to 800 x 600 x 16 M; with external monitor - 1280 x 1024 non-interlaced * 24-bit color provides up to 16 M brilliant colors 
-Video Memory  128-bit accelerated graphics with integrated 2 MB video memory 
-Hard Drive 4.3 GB Hard Drive   
-Diskette Drive    3.5 inch, 1.44 MB Diskette Drive 
-Multimedia Drive    24X Max CD-ROM Drive  24X Max  
-Display    13.0 inch HPA Display  
-Fax/Modem    56K ITU V.90 PCI Modem  ITU V.90  Network Card    Ethernet Network  
-Compatible Sound    JBL Pro Audio System 
-Programmable function keys (F1 and F2) Keyboard Full-size keys and separate cursor control keys (88 keys) 101-key compatible 
-Windows operating system keys 
-Pointing Device     Touchpad pointing device PC Card Slots          
-One Type II PC Card slot with support for 32-bit CardBus  External Ports 
-One (1) USB connector     
-Serial RS-232 compatible,  DB9 connector (16550) 
-Parallel SPP/ECP standard interface (DB25 connector) 
-PS/2 Mouse or Keyboard port
-R-11 modem jack 
-Two audio ports (headphone/speaker-out and microphone-in) 
-External VGA monitor port

---

### Post by AkiraBergman on 2009-12-21
I have the same problem with multiple linux installations on my PC with ASUS P7P55D-E mobo and SATA CD-ROM. This URL ties the problem to BIOS parameters;

[http://www.64studio.com/node/661](http://www.64studio.com/node/661)

The OSs I am trying to install are also amd64. I have not tried the proposed solution yet.

---

### Post by lostinxlation on 2009-12-21
Is that machine capable to boot from CDROM ?
 
BTW, 64MB is a little too small to run Xubuntu, I guess. I installed Xubuntu on my laptop which has 300MHz and 128MB system a week ago and it was too slow so that I had to go with other distro.

---

### Post by AkiraBergman on 2009-12-21
I thought you were using the live-CD method of installing. My problem is that although the system reads the OS from the CD drive, it fails to know what that drive is somehow. Maybe your case is different.

---

