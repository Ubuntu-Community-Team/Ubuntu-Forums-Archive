---
title: "Needing to install XP"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by memphisvol on 2005-06-01
Ok all, I already have Ubuntu installed and customized to my needs on my computer.  But in the last week or so, a few programs have come into me at work that I need to be able to run, and XP is the only option.  My question is, how would I go about installing XP without overwriting anything critical to Ubuntu, Or am I going to have to reinstall Ubuntu as well  ](*,)

---

### Post by bored2k on 2005-06-01
[QUOTE=memphisvol]Ok all, I already have Ubuntu installed and customized to my needs on my computer.  But in the last week or so, a few programs have come into me at work that I need to be able to run, and XP is the only option.  My question is, how would I go about installing XP without overwriting anything critical to Ubuntu, Or am I going to have to reinstall Ubuntu as well  ](*,)[/QUOTE]
 Install in a different partition. Then recover GRUB.
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

You could have also used the VMWARE OS emulator.

---

### Post by mingus on 2005-06-01
If you are comfortable with partitioning concepts and tools, there is another approach.  Basically you could copy Ubuntu to another partition, and then use hda1 (presumably where Ubuntu currently is) to install XP on.  You would then need to recreate GRUB's menu.lst control file and reinstall the boot loader.  If interested, post your drive's partition layout and sizing.

---

