---
title: "None of the kernel updates is working"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by freakzone on 2008-06-19
Hello,

I installed Hardy when it was released and I was using it without any problems till the kernel updates. The only kernel which is working on my system is 2.6.24-16. 17, 18 and 19 are not working. 19 for instance freezes on the login screen. 17 and 18 either do the same or freeze after I type the login. They freeze this way - while the system is loading and I see the mouse animation it just stops and then i have to restart from the reset button of the PC, 19 - when the login screen loads in the same instance the PC is frozen. 16 however is working without any problems.

My PC is AMD AthlonXP 2200+, 1.5GB DDR RAM, 20GB ATA Maxtor (for Ubuntu) and 250GB ATA Seagate (for Win and storage), Nvidia FX5500.

Can someone help me on this or at least tell me how to remove the non working updates from the bootloader.

---

### Post by housam on 2008-06-19
> **freakzone said:**
> 
 at least tell me how to remove the non working updates from the bootloader.

put # in front of each line of those kernels in the grub menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

---

