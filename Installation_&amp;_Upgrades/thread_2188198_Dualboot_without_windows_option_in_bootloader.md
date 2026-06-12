---
title: "Dualboot without windows option in bootloader"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by The Low End Theory on 2013-11-15
Hello, I would like to install Ubuntu alongside my existing Windows 8 install, but I want my PC to boot directly into Ubuntu without hitting a boot selection menu, is there a way to set this up so that I could run a command in Ubuntu to reboot into Windows?

Thank you.

---

### Post by oldfred on 2013-11-16
Is this UEFI or BIOS install?

Not sure with all the grub updates if this still works or not.

 Reboot grub to different system default
[http://ubuntuforums.org/showthread.php?t=1310463](http://ubuntuforums.org/showthread.php?t=1310463)
sudo grub-reboot 1
sudo grub-reboot "Microsoft Windows 7"

Title/Name must match exactly to system as found by os-prober. copy from here:
       gedit /boot/grub/grub.cfg

---

