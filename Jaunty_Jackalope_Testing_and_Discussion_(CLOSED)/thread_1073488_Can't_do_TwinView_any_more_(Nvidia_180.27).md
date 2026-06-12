---
title: "Can't do TwinView any more? (Nvidia 180.27)"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2009-02-18
OK - so I've previously been able to set up TwinView using nvidia-settings without any problems at all - enable the external monitor as well as my laptop screen, set them in the correct layout, apply, bingo.

Now, however, I get the error:
```
Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +0+0, DFP-0: nvidia-auto-select @1280x800 +1280+0' (Mode 2560x1024, id: 51) on X screen 0.
```I haven't touched anything. Any ideas? Tried running with gksudo nvidia-settings and same effect.

xorg.conf is a fairly plain affair, only adding Driver "nvidia" and "DontZap"

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerFlags"
    Option        "DontZap"    "off"
EndSection
```

Trying to disable laptop and go with just the external:
```
Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +0+0' (Mode 1280x1024, id: 52) on X screen 0.
```

This works fine on my EeePC and its Intel chip (running a USB install of Jaunty), so it's definitely down to Nvidia.

---

### Post by eyelessfade on 2009-02-18
just run xrand in a command shell, and then hit apply in nvidia-settings again. This is a workaround.

---

### Post by lithorus on 2009-02-18
> **jfernyhough said:**
> This works fine on my EeePC and its Intel chip (running a USB install of Jaunty), so it's definitely down to Nvidia.
Actually it could also be down to the Xorg developers.

See : 
[http://lists.freedesktop.org/archives/xorg/2009-February/043402.html](http://lists.freedesktop.org/archives/xorg/2009-February/043402.html)

---

