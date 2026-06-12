---
title: "Screen flickering when typing (KDE)"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by super.rad on 2008-10-27
Been using Intrepid since the first beta came out and had both gnome and KDE installed, gnome has always been fine but whenever I type in KDE I get flickering lines all over the screen and occasionally on closing a program the whole screen goes black for a few seconds and then returns to normal. The flickering is so bad it's making KDE unusable. I tried to record it using recordmydesktop but the flickering doesn't show up on there. It is only kubuntu that does it as gnome works fine and also using KDE on anyother distro is fine.
My graphics card is the following:
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```I tried a fresh install of kubuntu intrepid RC this morning and the problem is just as bad. 
I haven't made any changes to Xorg.conf and have checked Xorg's log and cant see any errors or messages that could be to do with this.
Any ideas on how to fix this?
EDIT: Thought it might help to post my xorg.conf
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

