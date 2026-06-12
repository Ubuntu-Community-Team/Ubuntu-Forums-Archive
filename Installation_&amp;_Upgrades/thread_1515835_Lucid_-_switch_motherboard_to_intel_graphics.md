---
title: "Lucid - switch motherboard to intel graphics"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by flammie on 2010-06-22
My old motherboard with integrated nvidia graphics died, and I just got a new motherboard with intel graphics.  It is a G41.  When I tried using Jockey to get graphics drivers, it says none are found and I can't enable desktop effects.  Does anyone know what I am missing?  I am on lucid and here is what is in my xorg.conf:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
#    Load    "glx"
#   Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver "intel"
#    Driver    "nvidia"
#    Option "RandRRotation" "true"
EndSection

---

