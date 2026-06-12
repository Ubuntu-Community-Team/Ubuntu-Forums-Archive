---
title: "FYI - Virtual PC 2004/2007"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by QuickFix on 2006-10-27
FYI - If you plan on checking out the latest "great" build of Ubuntu using Virtual PC and LCD monitors...there is a setting for color depth that defaults to 32 which may cause your screen to be garbled or have vertical, colorful lines and pointer.   Run "sudo nano /etc/X11/xorg.conf" from a command line after booting up in safe mode and change the Default Depth parameter in this section to "16"

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection

Reboot, and you're off to the races!

M

---

### Post by waynep on 2006-10-27
I am trying to do just this. Install 6.10 under VPC 2007. When I installed 6.06 I used the Safe Graphics menu choice from the ubuntu CD to get started. Trying the same thing on the 6.10 CD does not work. It defaults to the 32 bit depth which is garbled. 

How do I get it to boot in 16 bit depth so I can do the install?

wayne

---

### Post by rhenriksen on 2006-10-30
Many thanks - My virtual machine was booting into 1600x600x8, garbled. I particularly appreciate not just learning the file edit required, but *how* to get into an editor to make the change. Us total newbies need that sort of hand-holding.

RNH

---

