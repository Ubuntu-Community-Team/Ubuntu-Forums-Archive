---
title: "high cpu due to Xorg and choppy video playback with nouveau drivers"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by belgarth on 2010-03-23
I have an AN-M2HD motherboard that I did a fresh installation of Lucid beta 1. I am using the onboard 7050 chip. When I playback video in vlc or totem, there is high cpu in Xorg and the video is choppy. I have found a few mentions of choppy/jerky video with nouveau, but nothing definitive on the cause. I had a similar problem to this in previous installs using the nvidia proprietary driver. In that case I was able to fix the problem using the UseEvents Option, but that doesn't look to be a valid option with nouveau.

I tried using the xorg-edgers ppa as well and it didn't help.

Other than this problem 10.04 is working very well for me so I would like to get this one last thing figured out.

I would appreciate any help.

Brett

---

### Post by psyke83 on 2010-03-23
> **belgarth said:**
> I have an AN-M2HD motherboard that I did a fresh installation of Lucid beta 1. I am using the onboard 7050 chip. When I playback video in vlc or totem, there is high cpu in Xorg and the video is choppy. I have found a few mentions of choppy/jerky video with nouveau, but nothing definitive on the cause. I had a similar problem to this in previous installs using the nvidia proprietary driver. In that case I was able to fix the problem using the UseEvents Option, but that doesn't look to be a valid option with nouveau.

I tried using the xorg-edgers ppa as well and it didn't help.

Other than this problem 10.04 is working very well for me so I would like to get this one last thing figured out.

I would appreciate any help.

Brett

The nouveau driver is a completely different beast, so none of the driver options (save for the generic ones such as "RenderAccel") will be the same.

See "man nouveau" and "man exa" for help. An option which isn't documented, but I think is still valid, is:

```
Option "ExaOptimizeMigration" "true"
```

This improved performance on my system (for the intel driver before the change to UXA, and also with the radeon driver).

---

### Post by belgarth on 2010-03-23
Thanks for the advice.
I tried the 
Option "ExaOptimizeMigration" "true"
Unfortunately it didn't help much. It seems like the Xorg cpu usage improved a bit (from 80% all the time to 50% most of the time with spikes up to 80%), but the video is just as choppy.

---

