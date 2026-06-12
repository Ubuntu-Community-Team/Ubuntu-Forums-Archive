---
title: "Fire GL 9000"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gunksta on 2009-03-18
Using a fully updated version of Kubuntu, I'm noticing two problems, which I believe are related. I am using a Fire GL 9000 ATI card, which of course means I am having problems. Next time, I will buy Intel graphics, I promise.

1) My processor load is unusually high. Just sitting idle with HTOP running, it bounces from 2 to roughly 20%. It's an older Celeron, but still. This is odd. And no, it's not HTOP that's causing the bounce, it's X.

2) Repaint is __SLOW__. It's painfully slow and things are sometimes corrupted.

I have disabled KWin's desktop affects. Otherwise this system would be unusable. As it is, it is nearly unusable.

Obviously I can't install and use the proprietary ATI drivers since they appear to be borked.

I'm not real familiar with how Ubuntu now handles Xorg configuration. I would like to know which driver my computer is using. I suspect I may be using fbdev. I am going to write a short xorg.conf to force my computer to use ati, but I'm wondering if there is an easier way to check which driver I am using.

Running glxgears, my processor spikes to roughly 50% capacity, with glxgears taking up the vast majority of this. X uses most of the rest. This produces around 780 FPS.

The system has a gig of RAM in it, but at start-up, I'm only using about a quarter of this. RAM is not my issue.

I don't care too much either way about the fancy stuff, but I'd like to get my processor usage down so I can unplug it again (when needed) and I'd like to be able to maximize a window without a 2-3 second delay in getting a repaint.

Thoughts?

---

