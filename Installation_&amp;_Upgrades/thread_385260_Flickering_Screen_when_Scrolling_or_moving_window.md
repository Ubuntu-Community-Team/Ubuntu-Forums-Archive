---
title: "Flickering Screen when Scrolling or moving window"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Dart31 on 2007-03-15
Hello everyone and thanks for helping,

I have just installed Ubuntu Ultimate 1.2 which has Beryl already installed with it. 
Almost everything works fine but whenever I am moving a window(like Firefox), the window flickers white and slowly moves like an old time movie (if that makes sense).  
Also whenever I try to open the Beryl Window Manager the whole screen goes white and I can not do anything in Ubuntu. (If I Alt-Tab I can see my other open programs but it will not switch to them)

I am not sure if this is just a graphics card problem? Do I need to update the graphics drivers or do I need to buy a new graphics card? (which I would not like to do) The graphics info. is **NVIDIA GeForce 6150LE Graphics.**

If I need to update a driver can you also let me know where or how to update it since I am pretty new to Ubuntu and Linux.

Below is the information on the computer I believe the graphics card is built into the mother board as well.

Thank you again for helping,
Daniel

Processor: AMD Athlon 64 Processor 3500+ with Enhanced Virus Protection, 2.2 GHz
* Memory: 512MB PC2-4200 DDR2 SDRAM memory, 2 DIMM (240-pin, DDR2) (occupied)
* Hard Drive: 160GB (7200 RPM) Serial-ATA (SATA) hard disk drive
* Optical Device: LightScribe Double/Dual Layer 16x max DVD R/RW drive with CD writer capabilities: 16x DVD R, 8x DVD+RW, 6x DVD-RW, 8x DVD+R DL, 4x DVD-R DL, 16x DVD-ROM, 40x CDR, 32x CDRW, 40x CD-ROM
* Expandibility: 3 PCI slots (3 available), 1 PCI Express slot (available)
* Audio: Integrated Audio, 6 speaker configurable
* Graphics: NVIDIA GeForce 6150LE Graphics with TurboCache supporting up to 256MB shared video memory

---

### Post by chewearn on 2007-03-16
```
glxinfo | grep rendering
```

If you get "direct rendering: No" then nvidia driver is not properly installed.

---

### Post by Dart31 on 2007-03-16
I just type this code into the Terminal right?

When I type this into the terminal and hit "enter" I get this error.

@Ubuntu:~$ glxinfo | grep rendering
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

Let me know if I am doing something wrong or if there is something else to do to get this working.
Thanks,
Daniel

---

### Post by chewearn on 2007-03-16
Ok, just a guess here: you might not have sufficient graphics memory.

Based on the specs you provided, I see that you are using onboard/integrated graphics, right?  You have 512MB SDRAM on your motherboard, the onboard graphics can use up to 256MB.  How much memory do you actually allocated to the graphics?  (you can check that in the BIOS; or if you have nvidia-settings installed, you can also see the memory used):
```
nvidia-settings
```

But, again, this is just a guess; maybe someone wiser might be able to give a better analysis.

---

