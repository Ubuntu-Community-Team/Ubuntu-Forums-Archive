---
title: "but getting after ubuntu studio logo during boot this black screen:"
date: 2021-09-23
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2021-09-23
Tried ubuntu studio 21.04 ISO burn in a DVD DISK in a PC to boot from DVD: 
but after getting ubuntu studio logo during boot, this black screen APPEARED:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289186&stc=1[/IMG]

SEE ATTACHMENT... well?

PC is Quad core 2 / RAM 8GB / HP 

[COLOR=#3E3E3E][FONT=HPSimplifiedLight][COLOR=#000000]**Product: **HP Pavilion Elite M9372.Gr Desktop PC 2008-2009[/COLOR]
[COLOR=#000000]**Operating System: **Microsoft Windows 10 (64-Bit)[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]HP Pavilion Elite m9372.gr Desktop PC 2008-2009

[/FONT][/COLOR]
[IMG]https://1drv.ms/u/s!Aty5ebD9Y5-uiOc5JFvTaKvts3VRsA?e=UpEWXR[/IMG]

---

### Post by Bashing-om on 2021-09-23
lsepolis123 Hello

A graphics driver problem is a reasonable assumption.

Let's force to the fall back driver and see what results.
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit;
Try "nomodeset" at this time; 
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

If you get to a GUI with "nomodeset" we see what the hardware situation is and a possible driver install.

[INDENT]do what we can
[/INDENT]

---

### Post by MAFoElffen on 2021-09-26
@Bashing-om

That system has an ATI Radeon HD5770 and a motherboard Integrated Intel HD57 GPU. If the ATI card is still in the PCVIe x16 slot, then the Intel GPU is disabled. Have him try to start with  "radeon.modeset=0"...

---

### Post by Bashing-om on 2021-09-27
MAFoElffen; Thanks

Good to know and keep in mind.

appreciate too that you continue to have our back.

-together we can, and do-

---

### Post by lsepolis123 on 2021-10-28
FYI
GRAPHICS CARD IS
NVIDIA GeForce GT 730 2GB

I think VM/VirtualBox boot of Ubuntu Studio 21.04 or 21.10, is better and easier, in Windows 10 Home, host OS... I think I will give up the dual boot, because is also a risky task...

---

### Post by MAFoElffen on 2021-10-31
Since NVidia... Use "nomodeset"

---

