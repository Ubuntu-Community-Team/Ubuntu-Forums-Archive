---
title: "Screen gets scrambled on instalation"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by bakedpotatoe on 2010-04-29
Flow:

1. get correct iso for ubuntu 9.10
2. burn iso on usb using universal usb installer
3. reset pc
4. select usb as boot device in bios boot popup
5. ubuntu main install menu displays
6. install on this pc
7. command lines running around
8. installation options screen should appear (one I see when i run it over ms virtual pc)

ISSUE:

at point 8. i get screen with vertical yellow and green stripes, looking like something Vivienne Westwood patched up for afternoon cup of vodka. 

Samsung monitor displays warning dialog "Recommended resolution 1280x1024 ?". 

ALT+F5 and ALT+F6 switch display between stripes (1) and half screen being gray, other half green (2). Other ALT+F<xx> combination do nothing. 

CD installation comes to same. 

System info:

Mainboard :    Asus M2N-CM DVI
Chipset :    nVidia nForce 560
Processor :    AMD Athlon 64 X2 5000+ @ 2600 MHz
Physical Memory :    2048 MB (2 x 1024 DDR2-SDRAM )
Video Card :    NVIDIA GeForce 7025 / NVIDIA nForce 630a 
Hard Disk :    ST3300831AS (300 GB)
CD-Rom Drive :    SanDisk U3 Cruzer Micro USB Device
DVD-Rom Drive :    HL-DT-ST DVDRAM GSA-4163B
Monitor Type :    Samsung SyncMaster - 19 inches
Network Card :     MCP67 Ethernet
Operating System :    Microsoft Windows XP Professional 5.02.3790 Service Pack 2 (x64)
DirectX :    Version 9.0c  (october 2006)

Note: This is my 1st time trying to install Ubuntu. No idea why it works on Vitrual PC and not when I do it from bootable CD or USB.

---

### Post by fwoncn on 2010-04-30
nearly the same problem here.
the motherboard chipset is the originator

there is a bug report related to this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443113](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443113)
but no fixed yet :(

subscribe to this bug if you confirm it has something to do with your problem

---

### Post by bakedpotatoe on 2010-04-30
ah, thats it for ubuntu and me for now... prority/severity medium, assigned to no one... reminds me of my ex-ex-company lol

---

