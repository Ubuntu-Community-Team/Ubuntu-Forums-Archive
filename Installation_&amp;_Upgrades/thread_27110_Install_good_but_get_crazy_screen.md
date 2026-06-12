---
title: "Install good but get crazy screen"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by ooZAFLE on 2005-04-14
hey there... I just installed Ubuntu and no problems but after it loads everything up and tries to load the GUI it covers the screen with weird colors and shapes... I can tell it loaded gnome because if i click around and hit keys it makes sounds but the screen is realy messed up... is this and xorg, or video card problem. I'm running an nvidia 6600gt and it does this on the amd64 and x86 discs... and helpful hints would be awesome... I would love to try this distro but I'm sorta confused about this problem. thnx in advance

---

### Post by heimo on 2005-04-15
What I'd do is go to console (CTRL+ALT+F1) and reconfigure xorg.
```
sudo dpkg-reconfigure xserver-xorg
```
 
You may get hints from this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")
 
Sounds like you could have wrong or not working graphics driver. If you're using nv try nvidia (and vice versa). To use nvidia you need to add 'restricted' to sources.list and install nvidia-glx. All this is explained in unofficial Ubuntu guide.
 
[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/")

---

