---
title: "Enter bios key no longer works"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by MadMax2 on 2013-12-17
I have been trying to do a clean install of 13.10 but don't have dvd player so am trying to boot by USB.
USB isn't mentioned in bios but the motherboard manual says it is bootable by USB.
I have been trying to enter bios to look at the hard drive order to see if USB is included there (I read something along that line).

Earlier I had tried Plop but couldn't get it to work.
I had to repair Grub and I did a purge and reinstall of Grub. 
Now it boots to a Grub menu.
I thought the bios key was part of firmware?

---

### Post by raja.genupula on 2013-12-17
what Laptop/System you do use ?

---

### Post by MadMax2 on 2013-12-17
In this case it is a Compaq Presario SR1600AN Desktop PC 
Base processor
Sempron (P) 3200+ 1.8 GHz

    1600 MT/s (mega transfers/second)
    Socket 939

Chipset
ATI Radeon Xpress 200
Motherboard

    Manufacturer: MSI
    Motherboard Name: MS-7184
    HP/Compaq motherboard name: AmethystM-GL6E
----------------
I've tried F10, Del but it boots to screen:
GNU Grub Version 2.00-7ubuntu11
Ubuntu
Advanced options for ubu nut 
etc

---

### Post by ajgreeny on 2013-12-17
Make sure the USB is plugged in when you go into the BIOS with Del key, and you may find the option to boot to USB appears in the list.  There may also be a keypress to go to a boot priority list without entering the BIOS setup, but that key will differ depending on the mobo and BIOS that you have.
Try F2, F9, F11, F12, etc etc. it could be any of them but should say in the mobo manual, if you have one.

---

