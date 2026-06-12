---
title: "Low resolution after Feisty update *SOLVED*"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by CD Baric on 2007-08-10
nVidia MX400 card with nVidia legacy proprietary driver:

After installing Ubuntu 7.04, I only had 1024 x 768 resolution so I edited the /etc/X11/xorg.conf file as follows:

sudo pico /etc/X11/xorg.conf

I then found the section that looked like this:
(the dots mean 'and so on')

Section "Screen"
     Identifier     "Default Screen"
     Device         "nVidia Corporation NV11 [GeForce2  MX/MX 400]"
     Monitor        "Generic Monitor"
     DefaultDepth    24
...
    SubSection "Display
                   Depth      24
                   Modes     "640x480"  "800x600"  "1024x768"
     EndSubSection
EndSection

I just added  "1280x1024" into Modes so it looked like this:

Section "Screen"
     Identifier     "Default Screen"
     Device         "nVidia Corporation NV11 [GeForce2  MX/MX 400]"
     Monitor        "Generic Monitor"
     DefaultDepth    24
...
    SubSection "Display
                   Depth      24
                   Modes     "640x480"  "800x600"  "1024x768"  "1280x1024"
     EndSubSection
EndSection

After a reboot I had the higher 1280 X 1024 that was the native resolution of the Dell 19" monitor.

After letting Feisty update I was left with 102 x 768 resolution again.

After checking out the /var/log/Xorg.0.log I found that the updated Xorg server was using EDID (a monitor information query and system) and was getting an incorrect frequency reading.

The solution was to tell the Xorg server to ignore the EDID by editing the /etc/X11/xorg.conf file again - use the same command as above to open the file and then add Option "UseEDID"  "False" to the "Screen" section as follows:

Section "Screen"
     Option        "UseEDID"  "False"
     Identifier     "Default Screen"
     Device         "nVidia Corporation NV11 [GeForce2  MX/MX 400]"
     Monitor        "Generic Monitor"
     DefaultDepth    24
...

Save and reboot.

Now I had the full monitor resolution once again - Ain't life grand!

CD 'Bar' Baric

---

