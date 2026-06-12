---
title: "Wubi/Xubuntu 9.10 boot problem"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by sponge808 on 2009-11-13
I have a Dell Inspiron 2650 laptop with WinXP (32-bit).  I downloaded the Wubi installer and chose the Xubuntu 9.10 option.  After the first reboot, Xubuntu froze before completing the boot sequence.  I finally got it to boot by choosing the "ACPI Workaround" option (I think that's what it was called) in the GRUB menu.  The setup completed and after rebooting again, the computer froze at the same place as before, after displaying the following 2 lines:
```
[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0xb7ec000, size=0x787dc8]
```No error message or anything.  When I tried to boot in recovery mode, the boot sequence froze after the following line:
```
[  0.161751] pci 0000:00:1e.0:  PREFETCH window: 0x10000000-0x15ffffff
```Is there anybody who can help me with this problem?  I searched the forums but I couldn't find anything about this.

---

### Post by sponge808 on 2009-11-14
Nobody?  I guess I'll have to stick with XP for now.

---

### Post by super gaga on 2010-03-04
try jolicloud 

[http://www.jolicloud.com/](http://www.jolicloud.com/)

i had a similar problem and installed it in safe mode

[http://www.jolicloud.com/guides/jolicloud-express#safe-mode-installer](http://www.jolicloud.com/guides/jolicloud-express#safe-mode-installer)
 
it worked!!!

---

