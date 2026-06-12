---
title: "Installing Ubunutu on new Computer"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by ataylor1988 on 2007-05-07
I am trying to install Ubuntu 7.04 on my new desktop.  It is an AMD 64 3500+ socket AM2, Nvidia 6150 chipset with onboard video.  512meg ram.  I get it installed then go to run it, and all it will let me use is the Terminal the X windows system will not load.  I thought i found the correct driver on nvidia's website but when i went to install it said it didnt work with that kernal.  Is there anyway to do the driver update feature u use in the GUI from terminal.  Thanks. Andrew

---

### Post by bulldog on 2007-05-07
Install linux restricted modules for your kernel, and then the nvidia-glx-new driver from the repositories.

To find your kernel```
uname -a
```
You get something like ```
Linux AMD64 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

To install restricted modules```
sudo aptitude install linux-restricted-modules-2.6.20-15-generic
```
Use your kernel of course.

To install the nvidia driver```
sudo aptitude install nvidia-glx-new
```
Make sure the xorg.conf list the driver as nvidia instead nv
```
gksudo gedit /etc/X11/xorg.conf
```
Look at this part```
Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia" **<======** HERE
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

If this is correct reboot.

---

