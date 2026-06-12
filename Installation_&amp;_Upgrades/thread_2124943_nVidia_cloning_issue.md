---
title: "nVidia cloning issue"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by Viper187 on 2013-03-12
Ubuntu 10.04 32-bit with a geforce 8600GTS and current nvidia drivers+nvidia-settings....  Problem is I'm trying to clone on 2 monitors that are different aspect (1 is 16:9, the other is 16:10). No matter what resolution I try to set it seems to apply the same resolution to both because one screen is cut off. If I use 1920x1200 the bottom is cut off the 16:9, obviously. However, it makes no sense that the 16:10 screen is showing 1080P with the right side cut off despite the fact I used to play Xbox/PS3 1080P fine with the damn thing. It seems like the card/drivers are refusing to clone at 2 different resolutions, but I know both screens are capable of 1080p. Any ideas?

---

### Post by MAFoElffen on 2013-03-12
If you use "RightOf", which also is +0+0 then +1024+0.... then the resolutions have to be the same. Max resolution will be to the lesser of the two monitors. Has to do with the virtual terminal size, which, if you are going panoramic (width) is twice the width and once the height.... or width and twice the depth for under. So, yes the res needs to be the same on both, which sets the aspect ration as the same.

If you separate the screens out to different/separate screens , tied to ports and resolutions, of the same screen (or mirrored), instead of a continuation of the screen, then you can set each to a different resolution. 

Ubuntu's screen util, nVida settings and AMD/ATI utils all work this way. Otherwise parts of that virtual terminal will be "off" the screen of a monitor.

Does that make sense now?

EDIT--
Although... If you set the monitors to different aspect ratios (tied to ports) that still result in the same height, then you could tweak that. (widescreen mated with a normal monitor)

---

### Post by Viper187 on 2013-03-12
> **MAFoElffen said:**
>   If you separate the screens out to different/separate screens , tied to ports and resolutions, of the same screen (or mirrored), instead of a continuation of the screen, then you can set each to a different resolution.   Does that make sense now?   Not really. That's what I said I'm trying to do, but it refuses to work. I'm trying to output the same thing on both monitors (clones), but one is 16:9 and the other is 16:10. To my knowledge, both support 1080P, but the 16:10 one is cutting off the right side.  I literally do the same exact thing on my other machine (64-bit Ubuntu 10.04), but it refuses to work on this one for no apparent reason. Edit: Finally got it. I don't even know what was wrong, but it started working with both set to 1920x1080 like I thought it should.

---

### Post by MAFoElffen on 2013-03-12
can you post your xorg.conf within codes tags please?

---

