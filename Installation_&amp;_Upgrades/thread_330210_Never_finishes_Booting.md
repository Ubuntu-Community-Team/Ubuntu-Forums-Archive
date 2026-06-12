---
title: "Never finishes Booting"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by kd7jit on 2007-01-02
I downloaded the Ubuntu 6.10 today and burned the ISO. no problems there

I tried to just boot it as a live disc and I have issues everywhere. No matter what graphics mode I try ubuntu does not display correctly at the load screen, dim, wraped around and offset, etc. 

Here is my original system configuration:

[INDENT]System Summary 
 
System Type: Dimension 4100 
 
Quantity Parts # Part Description 
 
1 2336V CARD (CIRCUIT), PLANAR (MOTHERBOARD), NO SOUND, DIMENSION, 4100, A 
1 657WP PROCESSOR, 80526, 1GHZ, 256, 133, FIBER CHANNEL 
1 35KKW KEYBOARD, 104, 6P, UNITED STATES, SILITEK, RUBBERDOME, SMALL BOX 
1 886MJ MOUSE, PERSONAL SYSTEM 2, 6P, 2BTN, WHEEL, MICROSOFT 
1 554WF DUAL IN-LINE MEMORY MODULE, 128, 133M, 16X64, 4K, 168 
1 1377P COMPACT DISKETTE, BLANK, COMPACT DISKETTE WRITER, 1X/4X 
1 69JJP COMPACT DISKETTE, BLANK, COMPACT DISK RECORDABLE, 1-PK, 80MIN 
1 979NK COMPACT DISK READ WRITE, 680M, I, 5.25" FORM FACTOR, 8X, SONY, 1.0N 
1 8300V COMPACT DISK DRIVE, 128K, I, 5.25" FORM FACTOR, 20/48X, LITEON 
1 98483 CABLE, DORADO/ATHENS/TUALATIN/ALMODOR, COMPACT DISK DRIVE, ENHANCED INTEGRATED DRIVE ELECTRONICS, DUAL, KLINGER 
1 0C215 KIT, MODEM, V90, DATA FAX VOICE MODEMS, TITAN, DIMENSION, DELL AMERICAS ORGANIZATION 
1 5740C CABLE, AUXILIARY, INTERNAL, MODEM, 4C 
1 969NU MODEM, V.90, INTERNAL, DATA/FAX/VOICE, ASIA, LATIN AMERICA, NORTH AMERICA, TITAN 
1 181UR CARD (CIRCUIT), MULTI-MEDIA, AUDIO, CRTV-4780, FRONT AUDIO JACK 
1 57589 CABLE, AUDIO, MOLEX TO MOLEX 
1 73RGY CARD (CIRCUIT), VIDEO, 32MB, NVIDIA, M64, BASIC INPUT/OUTPUT SYSTEM 
1 688EN DISPLAY, MULTISCAN, COLOR, 17, DUAL, M781S, DELL AMERICAS ORGANIZATION 
1 7020T FLOPPY DRIVE, 1.44M, 3.5" FORM FACTOR, NO BEZEL, SONY, F/EJ3 
1 98480 CABLE, DORADO/ATHENS/TUALATIN/ALMODOR, FLOPPY DRIVE, KLINGER 
1 5828D ASSEMBLY, CABLE, ATA66, 2DROP, KLINGER 
1 871HK HARD DRIVE, 40G, I, 7.2K, 3.5" FORM FACTOR, 1N, NO CONTROLLER/NO CABLES, WD-XL20 
1 10RDC KIT, SOFTWARE, WKS-STE2K1, 5.25" FORM FACTOR, ORIGINAL EQUIPMENT MFGR., ENGLAND/ENGLISH [/INDENT]
 
the above is the orginal config for my machine

I have added 256 meg of RAM that passes memtest86

the AGP port on the computer is bad so I am using a PCI graphics card a Matrox Graphics Mystique PCI, old I know but it works fine under XP


so Here is my plea: HELP!!!  

Much Thanks

---

### Post by aberry5555 on 2007-01-03
This is quite a big problem that affects a fair few people but is easily overcome in a few ways. It happens because the preloaded driver on the CD doesn't work with your card, so you will either have to download the new drivers and use those or change to the "vesa" driver manually. 
[http://www.ubuntuforums.org/showthread.php?p=1961547#post1961547](http://www.ubuntuforums.org/showthread.php?p=1961547#post1961547)
Read my post on here to find out how to do it, once it's booted you should be fine.

---

