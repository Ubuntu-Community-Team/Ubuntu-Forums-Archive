---
title: "Install ubuntu on asus m2n-vm-dh"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by mrlillo on 2007-01-17
Im trying to install ubuntu on my new pc. It has a ASUS M2N-VM DH motherboard with and ASUS  DRW-1608P35  DVD burner. 
I tried installing with the desktop  i386 and 64bit version, but the installer hangs. Tried the i386 alternate version, and that seems to be working.
The problem is thath ange ubuntu doesent detect the cdrom drive. What should I write in field "PCMIA resource resource range options:" 

I cant find a spesific driver for my dvdrom , can anyone help me out?

---

### Post by Azuryn on 2007-03-15
Try disable the Jmicron SATA controller in BIOS settings. 
It works for me on another MB with this device on board and might be help for you.

---

