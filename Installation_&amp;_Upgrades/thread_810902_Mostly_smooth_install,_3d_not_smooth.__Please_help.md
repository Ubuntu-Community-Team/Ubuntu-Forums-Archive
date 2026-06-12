---
title: "Mostly smooth install, 3d not smooth.  Please help"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by seepage87 on 2008-05-28
Trying to upgrade from Gutsy broke my installation.  Not sure why, didn't test it.  I've been stuck in windows land because I was too busy to install fresh until today.  It seemed to go mostly smooth, but after enabling the restricted drivers for my ATI card, I get the 3d effects to work with compiz, but it isn't smooth, like the frame rate is really bad and it's struggling.  Not only that, when I switch tabs in firefox, it takes a whole second before it shows the tab I switched to.  Things are not smooth at all.

Is this a know issue?  Is there something I can do to make the ATI drivers work better?  Are there instructions for installing the latest ATI drivers under hardy?

---

### Post by Kemono on 2008-05-28
[_Yes, actually there are._](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by seepage87 on 2008-05-28
I tried "method 1" with its tweaks, etc, and no luck.  I'll try method 2 later and see if that helps.

---

### Post by Kemono on 2008-05-28
Actually, "Method 2" was the one I was telling you to try.

I used the older version of the driver but it was useless without the xgl server. I installed the newest drivers using the second method and everything is working fine...well, almost fine. Next time I'm getting nVidia.

---

### Post by seepage87 on 2008-05-29
Well, I have a new theory.  Method 2 doesn't seem to have helped, but it seems every time I start up some 800MB of my 1GB RAM are being used.  When I start firefox it goes ot about 950MB.  I didn't really notice it being that jerky until I started firefox, so this might be the problem.

Anyone have any ideas what could be eating so much RAM?  I seem to recall Gutsy not being nearly so resource intensive.  Any advice?

---

### Post by Kemono on 2008-05-29
Open "**System Monitor**" from **System>Administration** and see what's eating your RAM. I had a similar issue when I booted up. Turns out it was tracker (it was indexing my drives, which was consuming a lot of RAM).

By the way, what model is your graphics card?

---

### Post by seepage87 on 2008-05-29
It's a bunch of stuff.  Firefox takes up the most using 120MB, but the system monitor says only ~650MB are being used in total.  The system monitor applet for awn says another 320MB on top of the 650 being used are "cached", and about 20MB are used for the buffer and only ~20MB are free.  There's three instances of trackerd running, each using about 7.5MB, which isn't that much, all things considered.  I'm not sure what cached means in this context, or if that's an abnormally large amount.

---

### Post by Kemono on 2008-05-29
Linux **caches** your free memory, leaving it slightly above zero. The cached memory is used when an application requests RAM, thus receiving it faster. The cached memory is of no concern. It's not a bug it's a feature.

Seems there's a memory leak in AWN. Which is probably related to your drivers(since they don't work very well). Have you tried EnvyNG?

---

### Post by seepage87 on 2008-05-30
I'm don't think awn is the problem because the symptoms were there before I installed it.  Everything ran extremely well in Gutsy, I'm not sure what's causing the difference.  I'll try out EnvyNG, maybe I'll see some difference.  The problem isn't *that* bad in some senses, but every time I change tabs in fire fox or switch desktops or many other things, the system gets really choppy and rough.  I could just disable all compositing and stuff and it'd probably move smother, but one of the main reasons I use linux is because it's beautiful and graceful.  The visual responses to my actions make it a more enjoyable experience and more usable due to the feedback.

---

