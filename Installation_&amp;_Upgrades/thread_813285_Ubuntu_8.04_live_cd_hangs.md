---
title: "Ubuntu 8.04 live cd hangs"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by slow2.2sonoma on 2008-05-30
I have an Emachines T6524 and when I try to install Ubuntu through the live cd it will get to the loading screen where the bar goes back and fourth and then stay there for a while before crashing. I also tried to install without the live and it didn't work. I did successfully install inside of windows however I'd like to install it on its own partition properly.

I also have fedora core installed on its own partition and when I boot up Fedora Cores boot loader asks to chose between Fedora and WIndows, after choosing windows the WIndows Bootloader comes up and asks me to choose between Windows and Ubuntu, after choosing ubuntu Ubuntus boot loader comes up asking to choose between Windows and Ubuntu at which point I pick one. I basically want to end up with only Ubuntu's boot loader. I think once I get the Ubuntu Live cd to work I will simply uninstall Ubuntu from Windows inside the add/remove in Windows and then reboot into Ubuntu's Live cd and use its partitioner to delete Fedora and repartition with Ubuntu which should delete all the boot loaders except Ubuntu's if I'm correct. Does anyone know if this will work?

---

### Post by Sam Lars on 2008-05-30
I've had a lot of trouble with live CDs hanging...
When you get to the menu, there's an option at the very bottom to use different boot options.  Choose that.
There are lots of things you could try, such as
```
acpi=off
```
You can try looking around the forums for more.

---

### Post by slow2.2sonoma on 2008-05-30
Ok got the live cd working using "noapic acpi=off no pcmcia" now I', just installing Ubuntu over Fedora and simply need to uninstall Ubuntu from my Windows install.

---

