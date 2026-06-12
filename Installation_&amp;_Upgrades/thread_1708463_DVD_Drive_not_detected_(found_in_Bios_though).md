---
title: "DVD Drive not detected (found in Bios though)"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by randykahn on 2011-03-16
The brand new MEMOREX 24X Lightscribe DVD player(SATA) is not detected by my UBUNTU 10.10 install (via USB stick LiveCD install).
I know it should have worked out-of-the box, but it does not, dmesg or lshw command shows all other SATA connections ( 2 hard drives) , BUT the DVD Drive.
The DVD drive is detected by the MSI BIOS, it is also fully functional in the dual-booted Windos 7 installation next to the Ubuntu 10.10, so I know the DVD player is ok.

I have the latest B3 Stepping MSI P67A-GD65 motherboard with Intel i7 2600K cpu..
 
Hope someone can help ....

---

### Post by etnba on 2011-03-17
Hi,

I found a bug that Ubuntu 10.10 can't detect DVD drive when use SATA 3.0 port with IDE mode.
 
If the SATA controller was set IDE mode, please switch it to AHCI mode and try it again.
 
You can change SATA controller setting in BIOS.
 
BR

---

### Post by randykahn on 2011-03-18
Hi etnba,
Thanks to you, I stopped pulling my hair out and was able to figure out what was wrong.The new motherboard has 2 extra Hi-Speed SATA connectors ( twice the speed of the 3 gb/sec standard )...although the DVD drive is recognized by the Windows 7 dual boot, Ubuntu can't see the drive....The connectors look pretty much the same as the normal one's.
But after your post, it dawned on me SATA port and mode may be a cause...

So, a million thanks ...

---

### Post by Dutch70 on 2011-03-18
Nice work, both of you & welcome to UF.
Glad to see you've got it worked out.

---

