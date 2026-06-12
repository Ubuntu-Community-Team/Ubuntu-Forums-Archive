---
title: "Resolution problem SONY Bravia on ubuntu 12.04 64bit"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by cyclone_ on 2012-08-23
Hi,
I just did a fresh installation of an ubuntu 12.04 64bit but I am having problems with my resolution. The TV should be able to handle 1920x1080 @ 60hz but when when running a ```
xrandr -q
```I get
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1280 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1280x1024       0.0  
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0 
```The graphics card I use is: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6530D].
I am really a beginner here so any help would really be appreciated. 
Thanks

---

### Post by SeijiSensei on 2012-08-23
Did you install the proprietary driver for your Radeon?  Run the "Additional Drivers" application, and it will determine the proper driver then download and install it.

I have a Bravia connected to an NVIDIA-based card with a DVI<>HDMI cable.  It runs at 1920x1080 just fine when I use the custom NVIDIA utility to set the resolution.  I believe there's an equivalent application for ATI graphics.

---

