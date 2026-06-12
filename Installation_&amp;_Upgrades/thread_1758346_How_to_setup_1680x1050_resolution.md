---
title: "How to setup 1680x1050 resolution"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by aalex497 on 2011-05-14
Install recommended nvidia drivers
System > Administration > Hardware run (as root, from consolt) nvidia-xconfig edit /etc/X11/xorg.conf xorg.conf 

in my case works only **sudo gedit /etc/X11/xorg.conf**

Locate HorizSync and change it to 28.0 - 65.5

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "Unknown" 
    HorizSync       28.0 - 65.5
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

---

