---
title: "Missing higher resolutions after install (Sandy Bridge i5-2500K, VGA)"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by bergwelten on 2011-06-02
Hi everybody,

after installing Natty on my brand new shuttle with Intel's Sandy Bridge Core i5 (2500K), everything works fine except setting up a higher resolution fitting to my screen.

All I need is a 2048x1152 resolution, but all the display configuration in the hardware section of the system settings offers is 1024x768, 800x600, 848x480 or 640x480.

The monitor is connected via VGA since it doesn't have a DVI or HDMI plug.

Is there a way to tell the system there is more capability? Do I need a different driver? What and where can I check this?

Thank you!

---

### Post by bergwelten on 2011-06-02
Ok, I read on some other posts that due to the EDID policy not all monitors and especially with Intel graphic can be properly identified.

So there must be a way to tell the system about my monitor - in former versions it was the xorg.conf I had to configure, but in Natty I cannot find such a file in etc/X11/

Any suggestions?

---

### Post by bergwelten on 2011-06-02
It just doesn't work, just don't know exactly what to write into the xorg.conf. Here is my xrandr output, maybe someone can help me here:

[FONT=Courier New]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)[/FONT]

---

### Post by dfacto on 2011-08-18
Also having this problem on the new 2011 MacBookAir with i5-2557M.

---

### Post by steve11911 on 2011-08-19
This page details how to add undetected resolutions.Worked for me...

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

