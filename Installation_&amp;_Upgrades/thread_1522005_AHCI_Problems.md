---
title: "AHCI Problems"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by zachstauffer on 2010-07-01
Hi all,

on my notebook (Acer Aspire 1810T) I have Windows 7, and Ubuntu 9.04 installed. When I try to boot Ubuntu, it stops loading and will say something along the lines of "Gave up waiting for root device" (as seen in threads like this [http://ubuntuforums.org/showthread.php?t=1494274](http://ubuntuforums.org/showthread.php?t=1494274)).

The solution is to change the SATA controller in the bios to IDE. Then Ubuntu will boot, but Windows 7  will not. When I change it back to AHCI Windows boots, but Ubuntu will  not. I read that I could reinstall Windows so it will work in IDE mode, but I'd rather not do that, as it was installed by the manufacturer with all the correct drivers and such (laptops can be finicky).

Another solution, is to add "acpi=off" to the boot parameters. When I do so, it disables all the power saving features, it won't tell me my battery life, etc.

So I ask you, is there a way to get Ubuntu to boot in AHCI mode?

---

