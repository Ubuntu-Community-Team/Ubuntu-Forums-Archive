---
title: "Nvidia + Dual Screen issue in 9.10 (incorrect resolution on Monitor 2)"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by mbelos on 2010-01-17
Hey guys, I'm having issues trying to set my second monitor's resolution. I've installed the latest Nvidia drivers from the Nvidia website (190.53) and no matter what I try the second monitor's resolution is (max) 1360x768. Running xrandr gives me:

```

Screen 0: minimum 1024 x 768, current 2390 x 768, maximum 2390 x 768
default connected 2390x768+0+0 0mm x 0mm
   1366x768       50.0     51.0     52.0  
   2390x768       51.0* 
   1024x768       52.0 

```

I'm familiar with adding undetected resolutions with xrandr, but as you can see it doesn't look like I can add it to monitor 2 only.

My monitors are named (looking at the NVIDIA X Server Settings app): DFP-0 (laptop, primary monitor, max resolution 1366x768) and CRT-0 (secondary monitor, ASUS VW220T LCD)

My preferred resolution would be to have DFP-0 at 1366x768, and CRT-0 at 1680x1050.

I have a HP Pavilion DV6T-2000 with an Nvidia GeForce GT 230M.

lspci gives:
```
01:00.0 VGA compatible controller: nVidia Corporation Device 0a28 (rev a2)
```

Thanks for your help!

---

### Post by mbelos on 2010-01-18
Hey guys, I seemed to have fixed the issue... I reviewed my /var/log/Xorg.0.log file, and I found that the EDID was unrecognised on my 2nd monitor (CRT-0). I did some reading, and found that NVIDIA's drivers drop back to a "failsafe" mode for that monitor and guess the refresh rates. So, in my /etc/X11/xorg.conf file, I did this:

```

...
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    #HorizSync       28.0 - 55.0
    #VertRefresh     43.0 - 72.0
    #Option         "DPMS"
    HorizSync       31.3 - 80.2
    VertRefresh     56.0 - 75.0
EndSection
...

```

I commented out the default NVIDIA generated HorizSync and VertRefresh, and added in the ones I found on the monitor manufacturer's website.  I then added this as well:

```

...
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1680x1050 +1366+0, DFP: 1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
...

```

Once I rebooted, the 2nd monitor had all of the appropriate resolutions!

---

