---
title: "Need help with GRUB2"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2009-08-27
My test machine currently has both Windows 7 and Kubuntu 9.10 installed. I was trying to gain some insight into how to get the Windows bootloader to launch GRUB2 and totally lost the bubble.  

The recovery plan was to reload the Windows bootloader to get Windows 7 going again and then reinstall GRUB from the Kosmic Alpha4 LiveCD into the MBR of /dev/sda (where Win7 lives) and then update-grub to redetect and rebuild. 

The first part worked fine...the system will now happily boot Win7 till the cows come home, but when I boot from the Kubuntu 9.10 LiveCD I can't seem to get the correct command sequence to reinstall GRUB2.  I'd rather not do a complete reinstall just to be able to install the bootloader if that is possible, at this stage, but I need help.  Hints or pointers appreciated.

---

### Post by kansasnoob on 2009-08-28
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by rbmorse on 2009-08-28
Perfect. Thanks.

---

