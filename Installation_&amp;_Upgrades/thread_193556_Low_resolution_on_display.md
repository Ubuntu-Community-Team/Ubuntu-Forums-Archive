---
title: "Low resolution on display"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Rotta on 2006-06-10
I have recently bought a new computer (ECS nForce4 A939 with GeForce 7600GT) and with a LCD monitor.  This equipment should have support for a resolution of 1280 x 1024 in 65xxx colors @75Hz.

This works fine with a crisp and clear picture with SuSE 10.0, but it seems impossible to make Ubuntu accept these parameters - I always get 1024 x 768 resolution as highest alternative. How do I tell Ubuntu that I would like more pixels and less colors?

-Rotta

---

### Post by Dr. Nick on 2006-06-10
Well I may be able to help .

Edit your /etc/X11/xorg.conf file to include extra resoulitions by adding what is in red. Also to change depths change the number in blue. I didnt think refresh rate mattered on lcd's though?

After editing that file log out and see if the new options are avaible on the next login
```


Section "Device"
        Identifier      "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth   [COLOR=MediumTurquoise] [COLOR=RoyalBlue]24[/COLOR][/COLOR]
        SubSection "Display"
                Depth           1
                Modes           [COLOR=Red] "1280 x 1024" [/COLOR]"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes          [COLOR=Red] "1280 x 1024"[/COLOR] "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           [COLOR=Red] "1280 x 1024" [/COLOR]"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes          [COLOR=Red] "1280 x 1024" [/COLOR] "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes          [COLOR=Red] "1280 x 1024" [/COLOR] "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           [COLOR=Red] "1280 x 1024" [/COLOR]"1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by Rotta on 2006-06-10
That did the trick! :D Thank you very much and have a nice weekend everyone!
-Rotta

---

