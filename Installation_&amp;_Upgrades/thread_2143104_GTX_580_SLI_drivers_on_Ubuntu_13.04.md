---
title: "GTX 580 SLI drivers on Ubuntu 13.04"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by Arsic on 2013-05-07
Anyone have well written instructions on installing the drivers for a fresh, out of box install? 

My setup is with two monitors plugged into the same primary card, one DVI and the other HDMI as it should be. Every time I install the drivers, it doesn't render properly on both screens. It's the same behaviour I experienced when trying to install them on Ubuntu 12.04 and 12.10, which is of course, the Unity UI does not load.

I'm also installing it on an SSD, which I think makes it more difficult to click on the Unity elements due to the race issue.

---

### Post by oldfred on 2013-05-07
I have not done it, but these may help:

 ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)

---

### Post by Arsic on 2013-05-25
Thanks. I ended up using the first driver listed in the Software Center so it ended up working well enough with nvidia-settings after nvidia-xconfig as root.

Only problem now is the SSD, I can't click on any Unity elements or the title bar so I have to use a keyboard to navigate which is an awful pain. Any direction on that one?

---

