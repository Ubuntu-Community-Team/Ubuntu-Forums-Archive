---
title: "Intel 915 Graphics Adapter on Hardy"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by spamking2000 on 2008-08-21
Hey - Using Hardy on a friend's computer with an Intel 82915G video card... he has a widescreen monitor, but the only resolutions that come up are 1024x768, 800x600, and 640x480. Intel's site says that this card will do 2048x1536 at 85 Hz maximum resolution, and the widescreen monitor that it is hooked up to should do at least 1360x768... but I can't even seem to trick xorg.conf into going into that resolution... when going into System -> Preferences -> Screen resolution, I still only get the 3 lower resolution modes.

Any help would be appreciated!!

Thanks,
spamking2000

---

### Post by veloce on 2008-08-29
Sounds like you are using the earlier intel driver, are you using "intel" or something else?

With the earlier version you could install "915resolution" that would allow access to other video modes.  The later "intel" driver is supposed to allow access to all video modes.

---

