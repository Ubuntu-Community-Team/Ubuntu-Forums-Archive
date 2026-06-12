---
title: "Slow and jumpy after Ubuntu 18 upgrade"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by mrzx4p5-c4u6to-hwbqsl9 on 2018-09-06
Hello,

my desktop is very slow after upgrading to Ubuntu 18.

I suppose it could be the driver for the grafic card. lspci gives me:

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4290]
...
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R7 370 / R9 270/370 OEM]

Looks for me that there is not only my PCI grafic card, but an onboard chip as well, but I dunno which is which. 

And which driver should I install? I seem to have:
root@linux:~# dpkg -l *radeon*
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/halb konFiguriert/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/R=Neuinstallation notwendig (Status, Fehler: GROSS=schlecht)
||/ Name                                   Version                  Architektur              Beschreibung
+++-======================================-========================-========================-==================================================================================
ii  libdrm-radeon1:amd64                   2.4.91-2                 amd64                    Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                    2.4.91-2                 i386                     Userspace interface to radeon-specific kernel DRM services -- runtime
ii  radeontool                             1.6.3-1build1            amd64                    utility to control ATI Radeon backlight functions on laptops
ii  xserver-xorg-video-radeon              1:18.0.1-1               amd64                    X.Org X server -- AMD/ATI Radeon display driver

Hope this information is helpful, but surely I can provide more if needed.

Thanks for helping,
Andre

---

### Post by mrzx4p5-c4u6to-hwbqsl9 on 2018-09-07
Hm, after a restart the mouse pointer speed seems to be ok, no more stuttering.

glxgears gives me about 60FPS, should be more for Curacao PRO [Radeon R7 370 / R9 270/370, what do you think?

Kind regards
Andre

---

