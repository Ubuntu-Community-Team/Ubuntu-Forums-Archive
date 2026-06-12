---
title: "Nvidia driver installed, now color is off"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by wlentz102 on 2007-05-03
I have been a user of ubuntu for a while now, on and off, and I have come to love this distro.  Just wanted to let everyone know that. :)

Anyhow, I just installed 7.04 on my desktop, and the resolution was incorrect.  I read about the restricted drivers control panel, so I went ahead and installed the nvidia drivers. They installed just fine, I restarted, and I have my full resolution now.  However, the color is off, in a very weird way.  I've tried adjusting the depth, but it doesn't really make a whole lot of difference.

I have run the nvidia-settings tool, but it didn't really do a whole lot.  My monitor is connected via DVI cable.

I have an nvidia geforce 3 w/64mb ram.
AMD 2800+
1gb ram

Here's my xorg.conf: (i removed the mouse & keyboard info from below as I didn't think they were necessary for your purposes)
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce3"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "metamodes" "DFP: 1440x900_60 +0+0; DFP: 1440x900 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

I have posted a screenshot for your benefit.  Any help you can give me would be great.  I would love to be able to use the nvidia driver, but if I have to, I'll switch back to the nv driver.

Thanks,
Bill

---

### Post by wlentz102 on 2007-05-03
well, I got adventurous and restarted my computer, but using the VGA cable.  The colors came back!  The problem I have now is my screen looks fuzzy.  I checked the screen resolution, and it was set to 1440x900 (my monitor's best), and I auto-adjusted the monitor, but still it looked pretty fuzzy.  So I adjusted the refresh rate (which was at 50) to 55 (the maximum in the dropdown), and it looks fine!

One problem I notice is that the login screen is still fuzzy.  Is there a way to bump up the refresh rate all across the board?  I'm assuming that would be in the xorg.conf file?

---

### Post by tompa on 2007-05-03
I'm having the same problem I think. I'm using a Dell D800 laptop with twinview. After upgrading to 7.04 the colors on the external display connected via DVI got all messed up. The built in laptop display works fine though.

I'm using the nvidia driver with GeForce4 Ti 4200 Go AGP 8x.

Anyone knows how to fix this? I'll keep on looking for a solution....

/tomas

---

### Post by wlentz102 on 2007-05-03
I just took a look at the screenshot I took when I was using DVI, and it looks normal to me.  Strange.  (I'm using the VGA connection now)

---

