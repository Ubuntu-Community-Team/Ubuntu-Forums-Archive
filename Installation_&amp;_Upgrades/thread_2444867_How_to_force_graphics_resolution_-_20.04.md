---
title: "How to force graphics resolution - 20.04"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by davehk on 2020-06-05
Clean install of 20.04 on motherboard with intel graphics, driving two LG1710 4:3 VGA monitor via 1x displayport>VGA and 1X HDMI>VGA adapters. the Monitors are capable of 1280x1024 and I have an edid.txt file for them, but can't work out how to require it to be used. In 16.04 I put the following config in /usr/share/X11/xorg.conf.d/10-monitor.conf:

```
Section "Monitor"
  Identifier "Monitor0"  
  Modeline "1280x1024_60.00" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection
Section "Monitor"
  Identifier "Monitor1"  
  Modeline "1280x1024_60.00" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "CRT-0"
  Monitor "Monitor0"
  DefaultDepth 24
      Option         "CustomEDID" "GPU-0.CRT-0:/home/dave/edid.txt"
  Device "CRT-1"
  Monitor "Monitor1"
  DefaultDepth 24
      Option         "CustomEDID" "GPU-0.CRT-1:/home/dave/edid.txt"
  SubSection "Display"
    Depth 24
  EndSubSection
EndSection
```

But that doesn't seem to work in 20.04. ALso how do I restart the X-server - ctl-alt-backspace doesn't work like it did in 16.04.
I have to say that I find getting the displays working correctly is the hardest part of an ubuntu install - I am surprised it is so difficult, or am I missing something (always glad to learn).

Thanks,

---

### Post by CatKiller on 2020-06-05
> **davehk said:**
> I have to say that I find getting the displays working correctly is the hardest part of an ubuntu install - I am surprised it is so difficult

Well, that would be because of this: > via 1x displayport>VGA and 1X HDMI>VGA adapters. 

You're blocking off the part that enables it to all happen automatically. 

You may find that you have better luck by specifying HorizSync and VertRefresh rather than a modeline. You may also find it best to get each monitor working singly first rather than leaping straight to a dual-monitor setup.

---

### Post by davehk on 2020-06-05
Thanks  - yes, I realise that if I had native displayport and/or HDMI monitors it would all work automagically, but I am loathe to throw out two perfectly good VGA monitors if I don't have to - and I also have older systems that I still use that only have VGA outputs, so I still have a dual VGA switch to move between platforms.

I'll give you suggestions a try, thanks again.

---

### Post by davehk on 2020-06-06
Update: turns out it's not the dp/hdmi to VGA converters that are the problem, it's the ATEN 4x2 KVM switch. If I connect my VGA monitors directly to the aforementioned adapters, the system identifies the displays perfectly and all applicable resolutions are available in display settings and all works as expected. Now I have to work out how I'm going to organise switching between my three systems.

---

