---
title: "karmic and usb2vga issues (not working)"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jwmuelle on 2009-10-24
(This is a different problem than my other post on a xrandr issue.)

I've recently switched from fedora 11 to karmic and am tweaking my desktop config.  I've searched the forum and haven't seen anything relating to this situation.

I'm using Thinkpad T60 laptop with Intel 945GM/GMS graphics card for dualhead.  I also use a Tritton USB2VGA dongle for a third display.  Under F11, this worked with the same xorg.conf settings for serverlayout/screen/display/monitor.

Problem is that the 3rd display isn't getting a desktop or gnome panels displayed.  Only the default brown background, however the mouse/pointer is able to navigate to the screen.   The xorg.conf is configured to position this display to the left of my laptop/vga screen as shown here.  Screen 0 is the composite xrandr dualhead for laptop/vga.  Screen 1 is the USB2VGA screen.

/etc/X11/xorg.conf

Section "ServerLayout"
    Identifier     "triple head configuration"
    Screen        0    "Screen0" 0 0
    Screen        1    "Screen1" LeftOf "Screen0"
EndSection


Section "Screen"
    Identifier    "Screen0"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    4096 4096
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection


Section "Screen"
    Identifier    "Screen1"
    Device        "DevSisUSB"
    Monitor        "MonSisUSB"
    DefaultDepth    24
    SubSection    "Display"
        Depth 24
        Modes "1280x1024"
    EndSubSection
EndSection

Section "Device"
    Identifier    "DevSisUSB"
    Driver        "sisusb"
EndSection

Section "Monitor"
    Identifier    "MonSisUSB"
    VertRefresh    50-75
    HorizSync    30-90
EndSection

I appreciate any insights anyone has on this.

Thanks.
Jeff.

---

### Post by jwmuelle on 2009-10-24
I'm not sure why, but this has resolved itself.  

As I moved forward to test the new, experimental gnome-shell (from terminal window, gnome-shell --replace), the screens flickered, some errors displayed from gnome-shell, and the 3rd display came up with the gnome desktop (gnome-shell exited after the errors).

With this working, also tried xrandr with full resolution on 1st 2 screens (separate thread) and that was resolved as well.

Confirmed across 2 additional re-boots (without needing to try starting gnome-shell).

Jeff.

---

