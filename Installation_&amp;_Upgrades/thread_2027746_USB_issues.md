---
title: "USB issues"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by Werewolf6851 on 2012-07-16
Received a refurbished HP PC, so small only take up about quarter of the space inside the case.  power-brick power supply.
-
Referbished HP Pavilion p2-1013W PC
AMD Dual-Core Processor E-450


It came with Windows 7, installed between 3 partions.  Since step son needs windows for his games, figured just install /boot partion into usb thumb drive.  then use extended partions for the / /home and swap.  Using Alt install, expert mode, and nifty continue install from ssh line.  Only thing difference I say never saw message to install grub into mbr of partion or hdd.

Issue seems with usb thumb drive in slot, can't use usb keyboard to choose different boot device.  PC doesn't do anything till remove the thumb drive. 

I partioned the 4 gig usb drive to 500 mg /boot partion then rest as a /fat32 partion 

Wolf

---

### Post by Cheesehead on 2012-07-17
Using expert mode, you wouldn't see a bootloader prompt.

Expert mode assumes the expert has an unusual setup and will install the bootloader of choice, if needed, manually.

---

### Post by Werewolf6851 on 2012-07-18
Ah, okay.

Well part of the issue seems the PC didn't like have a usb thumb drive with more than 1 partion.  ie keyboard would not respond while it was plugged in.

Tried the 'expert mode' cause never used that before, and no risk, nothing learned.

Wolf

Tries again with fresh formated usbthumb

---

