---
title: "Stuttering gutsy performance, no shutdown buttons"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Muchacho_Gasolino on 2008-01-05
Kubuntu user, just updated to Gutsy from Feisty, and most everything is working fine, but it doesn't seem like I'm using the same computer. It seems to wear my computer out just dragging windows around and scrolling in browsers, terminals, etc. Sometimes while scrolling through a window, it will just hang and sit there for five seconds or so before deciding to continue. 

Startup and shutdown are reasonably quick and programs don't seem to have too much trouble loading. I just noticed, though, that my CPU is running at a pretty constant 67%, even though I am doing absolutely nothing right now besides typing this forum post. Physical memory use is up at 850MB out of my 1 gig, but that could be just residual from opening up firefox and thunderbird a couple of times.

Installing the proprietary ATI driver seemed to help things a bit. fglrxinfo tells me 

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)
```

, but glxinfo tells me No direct rendering. I feel like a lot of this might be a video problem. It seems like I'm getting no 2D acceleration. Can anybody help?

EDIT:
Forgot one thing: shutdown and restart buttons are gone. I had this problem while trying to get Beryl to work in Feisty, but I had it fixed before the upgrade, and I'm pretty sure that the upgrade uninstalled all that stuff anyway. I don't think I'm running an xgl server or any compiz stuff at all right now. How can I check and make sure of that?

---

### Post by Muchacho_Gasolino on 2008-01-06
Sorry for the unnecessary post; this thread fixed all my problems. Check on the section on what to do if you had XGL working in Feisty and upgraded.

[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)

---

