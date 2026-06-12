---
title: "toshiba 4080xcdt trident cyber 9225 xorg.conf"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by modergoose on 2010-02-07
Used weeks on getting my old laptop to show higher resolution. Finally found the solution. Create a xorg.conf file in /etc/X11-directory and copy this into the file:

Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "trident"
BusID "PCI:0:4:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-49
VertRefresh 43-72
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems Cyber 9525"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "800x600"
EndSubSection
EndSection

or copy the attachment to the /ect/X11 directory
Reboot and change the resolution under the display menu
Works on a toshiba satellite 4080XCDT with trident cyber 9525 display

---

