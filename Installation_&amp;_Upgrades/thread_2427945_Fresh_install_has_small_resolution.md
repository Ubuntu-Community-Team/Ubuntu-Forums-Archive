---
title: "Fresh install has small resolution"
date: 2019-09-27
forum: Installation &amp; Upgrades
---

### Post by noonecares on 2019-09-27
I'm new to linux and I'm trying to set it up to not use nvidia drivers but the Nouveau drivers just don't seem to work. On the first start up I check display settings and in the resolution drop down there is no options and if I do xrandr I get output of one resolution something like 680x460. 

Xserver and xorg Nouveau drivers appear to be installed when I check synaptic. From what I've read the default Ubuntu install should have decent drivers out of the box with Nouveau but no matter what instruction I follow online to update or install Nouveau I just dont see any results or I get errors 

I'm writing this on my windows os so I dont have any of the exact errors I'm getting but if you want me to run anything to see what I'm talking about I can. 

I have a RTX 2080 which I'm convinced is just to new to be compatible with Nouveau drivers. I'm using a desktop computer  

When I install Nvidia drivers it works perfectly. but I haven't installed them at all on this most recent install of Ubuntu.

---

### Post by CatKiller on 2019-09-27
> **noonecares said:**
> I'm new to linux and I'm trying to set it up to not use nvidia drivers

Why?

The nouveau driver is nowhere near as good as the proprietary one at detecting monitor resolutions, and is unable to increase the clock rate from the lowest state.

Unless you are a nouveau dev there is absolutely no point in not using the proprietary driver on an RTX 2080.

---

### Post by Autodave on 2019-09-27
My RTX 2070 runs just fine on the newest driver in the repos.

---

### Post by noonecares on 2019-09-27
did it work immediately after install or did you do something first?

---

### Post by slickymaster on 2019-09-27
*Thread moved to **Installation & Upgrades**.*

---

