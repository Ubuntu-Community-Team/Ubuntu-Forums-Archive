---
title: "fglrx apparently in use, but shown as inactive"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by quadproc on 2010-02-22
I finally reinstalled the fglrx driver in this system after having been using the "ati" driver since the upgrade to Ubuntu 9.04 and I notice what appears to be an inconsistency between the xorg.conf file, the results of the "hardware drivers" in system administration, and the behavior of the desktop.  Some details:

Ubuntu 9.04
Kernel 2.6.28-18 generic
GNOME 2.26.1
ATI fglrx driver:?:

Dual ATI HD4870 cards in crossfire configuration

When I run the system administration hardware drivers function, its window says "No proprietary drivers are in use on this system", then it lists the fglrx driver, and there is an indicator near the bottom of the window that says "This driver is not activated".  The driver was installed using the ATI .run script.

When I look into the xorg.conf file, I find```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```When I start processes which create a window (e.g., term) then I notice that effects happen: the window "fades in" and "telescopes in" to its final size in a matter of about 1/4th of a second. Likewise, terminating a window causes the window to "fade out" and "telescope out" in the same amount of time. This behavior is new; previously, with the "ati" driver, the window just snapped into existence with no effects.

The questions::confused:

What is going on?
Is the system actually using the fglrx driver?
Why do things disagree regarding the driver?

Thanks for any insights.

quadproc

---

