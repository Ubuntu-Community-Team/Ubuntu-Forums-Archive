---
title: "Screen resolution problem after upgrade to 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by globaljuggler on 2008-04-26
Upgrading to 8.04 went smoothly. However when I try to change the screen resolution I get the following error:

The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

Please help

Here is my xorg.conf file:

```
    Section "InputDevice"
       Identifier   "Generic Keyboard"
       Driver      "kbd"
       Option      "XkbRules"   "xorg"
       Option      "XkbModel"   "pc105"
       Option      "XkbLayout"   "se"
       Option      "XkbOptions"   "lv3:ralt_switch"
    EndSection

    Section "InputDevice"
       Identifier   "Configured Mouse"
       Driver      "mouse"
       Option      "CorePointer"
       Option      "Emulate3Buttons"   "true"
    EndSection

    Section "Device"
       Identifier   "Configured Video Device"
       Option      "UseFBDev"   "true"
       Driver      "fglrx"
    EndSection

    Section "Monitor"
       Identifier   "Configured Monitor"
    EndSection

    Section "Screen"
       Identifier   "Default Screen"
       Monitor      "Configured Monitor"
       Device      "Configured Video Device"
       Defaultdepth   24
    EndSection

    Section "ServerLayout"
       Identifier   "Default Layout"
      screen "Default Screen"
    EndSection
    Section "Module"
       Load      "glx"
    EndSection 
```

---

### Post by globaljuggler on 2008-04-27
Fixed. This command performed a miracle:

```
sudo apt-get remove xserver-xgl --purge
```

---

### Post by bitter_mike on 2008-04-27
This worked for me too. I went to Synaptic and did a "complete removal" of the package, then restarted the X server and the screen resolution app came up without a problem.

---

