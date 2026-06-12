---
title: "Kubuntu A3 compiz and emerald problems"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-02-03
Love the new theme for Kubuntu A3.
I'm using an Nvidia 7600GS card with the latest 180 driver (from the repos). Compiz and Emerald work fine in Ubuntu A3, but not Kubuntu A3 (with all updates to date).
In terminal, I get the following errors
```
$ compiz
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12image format
Couldn't find a perfect decorator match; trying all decorators
Starting emerald

(emerald:7903): Gtk-WARNING **: libbonoboui-2.so.0: cannot open shared object file: No such file or directory

(emerald:7903): Gtk-WARNING **: libbonoboui-2.so.0: cannot open shared object file: No such file or directory
```
No prompt is displayed after the last error.
My xorg.conf file:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```
I've installed ccsm and emerald via Adept.
ccsm seems to be incomplete as it is missing some options as well as icons when compared to the Ubuntu version (see attachment).

---

