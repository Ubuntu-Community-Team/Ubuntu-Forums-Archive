---
title: "A few oddities with Nouveau after upgrade to 10.04"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by rstoya05-lx on 2010-06-20
I upgraded from 9.10 to 10.4 this morning on my Dell Precision M2400 laptop. When I rebooted I got a half-black screen with lines. The top portion had 3 miniature login screens also with lines across and too tiny to see anything.

I looked at my xorg.conf. It had this in it:

```
Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 3360 1080
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

I decided to remove it as I've read it's discouraged and not necessary nowadays. After this I am getting a normal resolution. However, there are a few oddities. 

1. When I try to use Admin -> Display I get the warning:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Why do I get this prompt every time? I don't want to use the binary nvidia driver if that's what it means! 

2. In the Display settings dialog it says monitor unknown. No big deal but if I plug an external monitor and press "Detect monitors" nothing happens. This used to work fine in 9.10.

I find there is lots of information on configuring the binary nvidia driver (e.g. on help.ubuntu.com) but I don't want to use it. It's hard to find any help or tips on using Nouveau (do I need xorg.conf for example?), which I find strange because that is the default option.

---

### Post by rstoya05-lx on 2010-06-20
It looks like the upgrade installed a bunch of nvidia packages. That's a shame. If I didn't have them installed before the upgrade why would I want them after?

I removed all packages matching to nvidia-* that I could find in Synaptic Package Manager and rebooted. I could already see some progress because the second monitor was showing signs of life even though the resolution was wrong. 

I added back the original xorg.conf, restarted again, and was able to set both monitors to the right resolution in the Display settings. 

I find it strange that Ubuntu pushes proprietary nvidia drivers so hard especially given that the upgrade left my machine unusable at first and required half a day to get me back to normal. Seriously where is the logic in that?

You can read everywhere how quirky nvidia drivers are and it has been my experience too in the past. Good luck reading the convoluted FAQ or chasing down a bug. I'm fine with trading the features nvidia drivers provide for stability.

---

