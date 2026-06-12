---
title: "Ubuntu Studio freezes installing"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Glenster on 2007-06-23
Ubuntu Studio freezes when installing it. I have md5summed it like I always do, so there I can't see any problem.

This happens:
Everything seems to work alright, checking keyboard, read in the components, and so on. But after some kind of check of floppy drive, seems to be the second, it all freezes on a bluished screen with a grey bar at the bottom. No text is displayed during that freeze so I can't explain what's going on.

I do not have any floppy disk on that computer. I hope that's not a problem. Why should it? New computers don't have them anyway.

Anyone's having an explanation?

---

### Post by Caddrafter on 2007-06-23
> **Glenster said:**
> Ubuntu Studio freezes when installing it. I have md5summed it like I always do, so there I can't see any problem.

This happens:
Everything seems to work alright, checking keyboard, read in the components, and so on. But after some kind of check of floppy drive, seems to be the second, it all freezes on a bluished screen with a grey bar at the bottom. No text is displayed during that freeze so I can't explain what's going on.

I do not have any floppy disk on that computer. I hope that's not a problem. Why should it? New computers don't have them anyway.

Anyone's having an explanation?


Having problem on install, only I get to "Installed brltty-x11" at 85% and freezes!
I have tried re-install and it STOPS at the same location, tried the Broken install and it's the same!
Freezes at 85% after "Installed brltty-x11"!
Checksum is correct. 
:(

---

### Post by mrmg on 2007-06-27
I had this problem as well. It seems that my machine was actually trying to get the file from the internet. I was installing off line but did plug a cable in just when it was setting up eth0 so I'm not sure if it's related. Plugging the cable back in resolved the issue.

Just for info, you can press CTRL+ALT+F4 to see what the machine is doing while it installs. I was sitting there for ages before I tried to find out what was going on.

---

