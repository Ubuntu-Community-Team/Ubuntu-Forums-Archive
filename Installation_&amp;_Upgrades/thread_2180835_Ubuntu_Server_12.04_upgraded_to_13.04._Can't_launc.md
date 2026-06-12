---
title: "Ubuntu Server 12.04 upgraded to 13.04. Can't launch Gui"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by hitekwaiter-j on 2013-10-14
I've had an Ubuntu server which started with 11.04 and has been running 12.04 for sometime.
I upgraded it to 12.10. after that the "startx" command ran calls that froze

So, I upgraded to 13.04

my xorg.conf file is the same

I"m also running Ubuntu 12.04 Desktop, dual booting on the same machine.
The xorg.conf file located at /etc/x11 is as follows. This works fine. 
What do I need to do to install/start/run the gui in 13.04? thanks

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1024x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "1280 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2880 2880
        Depth     24
    EndSubSection
EndSection

---

### Post by ibjsb4 on 2013-10-15
If your running ubuntu-desktop, startx should default to it.

I run gnome-fallback so I had to create a .xinitrc in my home folder to run my desktop from the startx command.  Maybe this would work for you.  This is mine:

[ATTACH=CONFIG]246972[/ATTACH]
You will of course need to change it to the appropriate desktop command.  If your running ubuntu-desktop, I think it should read:

exec ubuntu

Not sure about that though.

[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

---

