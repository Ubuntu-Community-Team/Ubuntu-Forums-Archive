---
title: "[SOLVED] Just installed Ubuntu: nvidia-settings won't stick..."
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by gohanssjn on 2008-06-05
Specifically the Gamma setting, as my 7400go is set wat to high to start.  I saved the X config, but no luck.  And no where in the X config can I set a gamma setting.

When I boot, gamma is at 1.00, as soon as I start nvidia-settings, it jumps to .667, where it needs to be.

How can I make it apply at boot??

---

### Post by wolfen69 on 2008-06-05
try
```
gksudo nvidia-settings
```

---

### Post by gohanssjn on 2008-06-05
Nope, gamma is still not included :(

Is there a way to insert it into the Xconf?

---

### Post by gohanssjn on 2008-06-05
Solved!

Just inserted 

Gamma 0.667 into the xorg.conf under my current monitor.

---

### Post by kaibob on 2008-06-06
Glad you got things working. I had the same problem and, like you, had to insert the gamma manually into the xorg.conf file. Just in case someone happens upon this thread and wants to know how to do this, I've copied below the monitor section of my xorg.conf file. All you need to do is insert the gamma line with the three settings for red, green, and blue.

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1905FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Gamma           0.85 0.85 0.85
    Option         "DPMS"
EndSection
```

This did not entirely fix the problem for me, as the .nvidia-settings-rc file still contained the default gamma settings. So, I also changed these as follows:

```
# Attributes:
<snip>
0/BlueContrast=0.000000
0/RedGamma=0.850000
0/GreenGamma=0.850000
0/BlueGamma=0.850000
0/OpenGLImageSettings=1
```

I do not understand the relationship of the .nvidia-settings-rc and xorg.conf files as far as settings for the nVidia card, but making both of the above changes fixed things for me.

---

