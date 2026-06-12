---
title: "Windows repair without affecting GRUB"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by Marco_Ros on 2016-05-09
Hello,
before installing Ubuntu 14.04 SLT, I have installed Windows 7, and they worked well using dual boot, but something happened that Windows doesn't boot anymore and needs repairing, but I'm affraid dual boot gets lost.
Is there a procedure to do this?

Thanks a lot

SYSTEM:
Ubuntu 14.04 LTS 64 bits
Acer Aspire 2920
CPU: Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2 
RAM: 2GB
Graphics card: Intel® 965GM

---

### Post by oldfred on 2016-05-09
Most Windows repairs will restore the Windows boot loader to the MBR.
You just then need to reinstall the grub boot loader to the MBR with your live installer either with Boot-Repair or manually.

       [URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader
[/URL]
 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    [URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]
[/URL]

---

