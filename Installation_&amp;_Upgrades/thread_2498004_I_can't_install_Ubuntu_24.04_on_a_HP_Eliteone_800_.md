---
title: "I can't install Ubuntu 24.04 on a HP Eliteone 800 G3 AIO"
date: 2024-05-25
forum: Installation &amp; Upgrades
---

### Post by ne0ntiger on 2024-05-25
I have tried to install Ubuntu 24.04 several times, but when trying to load the bootloader it always ends up on a black screen, if I use the Ubuntu with safe graphics option I can enter the installation mode, when the installation finishes and restarts the computer it goes into a loop reset system and cannot start. I appreciate if someone could help me with this error

---

### Post by oldfred on 2024-05-26
If you needed safe graphics, did you also install the restricted/optional drivers. Not sure in Ubuntu exactly what it says, as I use Kubuntu, calls it now.
That will install the correct graphics driver for your system.

Then with HP, you have to either always manually boot from UEFI one time boot menu or go into UEFI settings (not menu) and change boot order.
Just depends on which system you want to use the most.
Grub will boot working Windows. But Windows fast startup/hibernation prevents that, so it must be off, if you want to boot Windows from grub.
And Windows may turn fast startup back on, so then you have to boot Windows from UEFI one time boot menu to turn off fast startup again.

HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)

---

