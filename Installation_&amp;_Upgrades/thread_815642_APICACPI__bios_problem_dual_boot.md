---
title: "APIC/ACPI  bios problem dual boot"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by joeyslc on 2008-06-01
If I have the BIOS set with ACPI  "on"  XP boots fine. If I have BIOS set with ACPI "off" Ubuntu 8.4 boots fine.  With it turned on Ubuntu gets an 8254 error msg and requests bug msg  then says to try booting with NOAPIC.
Also replies in error msg that there is a clock error can't sync timer ? 
I think it's the MB BIOS  and or MB  I'm running 3.20 dual core 2 gig mem
on a ESC MB model RC410L/800-M . Any clues to get a proper dual boot up and running would be great. P.S. same set-up works fine on an older system.As it stands now I have to change Bios setting every time I change operating systems.

---

### Post by Partyboi2 on 2008-06-02
Have you tried adding acpi=off or noapic as a boot option to your menu.lst? To do this open a terminal (Applications>Accessories>Terminal) and 
```
sudo nano /boot/grub/menu.lst
``` and look for the line starting with "# kopt=root=......." and add ```
acpi=off
``` or ```
noapic
``` then after you have saved (Ctrl+o) and exit (Ctrl+x) back in the terminal
```
 sudo update-grub
```

---

