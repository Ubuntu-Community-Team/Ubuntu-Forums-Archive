---
title: "How do I get full resolution on Ubuntu 13.10 in VirtualBox?"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by dean.w.schulze on 2013-12-31
The host OS is Windows 8 pro.  My monitor is 1920x1080.  When I install Ubuntu 13.10 in VirtualBox the highest resolution is shows in the Resolution drop list is 1024x768.  How do I get it to use the full monitor resolution?

I have Ubuntu 12.04 installed on a Windows 7 laptop with external monitor and I don't recall having any issues getting full resolution on that guest OS.  The seems like a new problem with the 13.10 distro.

Thanks.

---

### Post by kgfowler on 2014-04-23
There may be a more appropriate and/or elegant solution, but I chose to add an xorg.conf to /etc/X11.  Here's a copy of my xorg.conf forcing the "Screen" to match my 1360x768 monitor. Just change it to 1920x1080 and you should be set.

# START /etc/X11/xorg.conf:
    Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
    EndSection

    Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver      "vboxmouse"
        Option      "CorePointer"
    EndSection

    Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vboxvideo"
    EndSection

    Section "Monitor"
        Identifier      "Configured Monitor"
        Option          "DPMS"
    EndSection

    Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1360x768"
        EndSubSection
    EndSection

    Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
    EndSection
# END    /etc/X11/xorg.conf:

-kf

---

### Post by mastablasta on 2014-04-24
what you need to do to get full screen resolution is install virtualbox guest additions. see on virtualbox site how to do that.

---

