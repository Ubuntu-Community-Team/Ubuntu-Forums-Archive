---
title: "How do I correct overscan on my HDTV?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by jwatsonoz on 2008-01-02
Hi,

I have an LG HDTV connected by DVI/HDMI lead to my computer.

After much stress (had to disable EDID info as it misinformed) I have managed to set the widescreen resolution of 1280x720.

The problem I have is significant overscan. In windows xp this is easily corrected using sliders on the NVIDIA settings dialogue box. However, the linux NVIDIA settings program doesn't appear to have any sliders.

I have tried setting the resolution of my screen to 1176x684 (the custom resolution I set using the sliders in windows xp) and have used several 'modeline creators' that I found online. Unfortunately, every modeline I produce makes the monitor come up with "invalid format"

I'm new to Linux, but I feel I have got a a reasonable distance in a short time....however I must admit I need help! I've enjoyed the journey so far

thanks

PS.

supported display specs for my TV for 1280x720:
(Horizontal - KHz) / (Vertical - Hz)
37.5/50
44.96/59.4
45/60

---

### Post by gunja99 on 2008-01-06
Hi there. Thanks for the post on my post! Well, I have actually succeeded in getting mine running! I installed windows XP, and tried some utilities there to help with things in the end, but this still didn't fix my problem... It was very very simple in the end, and I feel so silly I could cry! I changed the zoom mode on the TV from 16:9 -> Just Scan (obviously this is a samsung TV, and not an LG), but try it! See what happens. I have now got XBMC working on the PC, and it's blooming fantastic, even tho it's in Alpha for Linux.

Unfortunately the intel drivers always use the EDID data, and theres noway to turn this off. I have however found some standard modelines you may want to try:

```
# 1920x1080p @ 60Hz (EIA/CEA-861B)
ModeLine "1920x1080" 148.500 1920 2008 2056 2200 1080 1084 1089 1125 +hsync +vsync
# 1920x1080p @ 50Hz (EIA/CEA-861B)
ModeLine "1920x1080" 148.500 1920 2448 2496 2640 1080 1084 1089 1125 +hsync +vsync
# 1920x1080p @ 24Hz (EIA/CEA-861B)
ModeLine "1920x1080"  74.250 1920 2560 2608 2752 1080 1084 1089 1125 +hsync +vsync
# 1920x1080i @ 60Hz (EIA/CEA-861B)
Modeline "1920x1080"  74.250 1920 2008 2056 2200 1080 1084 1094 1124 +hsync +vsync Interlace
# 1920x1080i @ 50Hz (EIA/CEA-861B)
Modeline "1920x1080"  74.250 1920 2448 2496 2640 1080 1084 1094 1124 +hsync +vsync Interlace
# 1280x720p @ 60Hz (EIA/CEA-861B)
ModeLine "1280x720"   74.250 1280 1392 1440 1648  720  725  730  750 +hsync +vsync
# 1280x720p @ 50Hz (EIA/CEA-861B)
ModeLine "1280x720"   74.250 1280 1720 1768 1984  720  725  730  750 +hsync +vsync
# 1440x576p @ 50Hz (EIA/CEA-861B)
ModeLine "1440x576"   54.000 1440 1464 1592 1728  576  581  586  625 -hsync +vsync
# 720x576p @ 50Hz (EIA/CEA-861B)
ModeLine "720x576"    27.000  720  736  800  864  576  581  586  625 -hsync -vsync
# 1440x480p @ 60Hz (EIA/CEA-861B)
ModeLine "1440x480"   54.000 1440 1472 1584 1712  480  489  495  525 -hsync -vsync
# 720x480p @ 60Hz (EIA/CEA-861B)
ModeLine "720x480"    27.000  720  736  800  856  480  489  495  525 -hsync -vsync
# 640x480p @ 60Hz (EIA/CEA-861B)
ModeLine "640x480"    25.182  640  656  752  800  480  490  492  525 -hsync -vsync

```

Anyways, good luck with getting Ubuntu/NVidia and HDTV working!

---

### Post by champracer29 on 2008-01-06
Can you give me insturction to put those codes in? I am not sure how I can get in to xorg.conf file.

Appreciate your help. Thanks!

---

