---
title: "Precise 12.04 doesn't detect monitor resolution"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2012-05-08
Hi,

I just upgraded from 11.10 to 12.04. The problem is that when I look into "System Settings"->Displays it shows a maximum resolution of 1152x864 when the monitor resolution is actually 1600x1200. However it recognises that is a Dell 20' monitor that appears written on that window. The machine is a Dell 8200 with a Nvidia GeForce FX5600.
I played a bit with the xorg.conf file trying to add the resolution with the following lines:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes "1600x1200"
    EndSubSection
EndSection

but it didn't help. After reboot the resolution is still not recognized. I also tried using the proprietary Nvidia drivers. I installed "nvidia-current" and it didn't help, and when I attempted to try with "nvidia-173" it came back with a message of broken packages that is only shown when I attempt to install that driver. After unmarking that package, the system says that there are no broken packages. Even without the nvidia drivers, shouldn't the system be able to detect the correct resolution? I'm attaching the Xorg.0.log file. Many thanks in advance.

Daniel

---

### Post by danielsender on 2012-05-08
Anybody? Thanks!

---

