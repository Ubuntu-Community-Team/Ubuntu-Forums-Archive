---
title: "Unidentified Monitor Upgrading to Ubuntu 10.10"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by dougw4 on 2010-12-04
I realise that there is more than one way to fix unidentified monitor problems when installing Ubuntu, but this xorg.conf file is what worked for me. It's based on the failsafe version of xorg.conf. It's short and simple. So it should be easy to modify for other monitors.

```
# xorg.conf
# This works for me in Ubuntu 10.10.
Section "Device"
  Identifier "Configured Video Device"
  Driver     "vesa"
EndSection

Section "Monitor"
  Identifier "Configured Monitor"
  Vendorname "Sony"
  Horizsync 31.5-48.0
  Vertrefresh 56.0-85.0
EndSection

Section "Screen"
   Identifier "Default Screen"
   Device     "Configured Video Device"
   Monitor    "Configured Monitor"

   SubSection "Display"
      Modes "800x600" "1024x768" 
   EndSubSection

EndSection
```

---

