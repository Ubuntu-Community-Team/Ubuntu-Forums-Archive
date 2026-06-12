---
title: "[SOLVED] URGENT - &amp;quot;invoke-rc.d: initscript gdm, action 'reload' failed.&amp;quot;?"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2008-06-16
GDM is crashing, attempting to restart, and then crashing again repeatedly. I don't knbow what's happening, but when I try ```
sudo dpkg-reconfigure gdm
``` it tells me > invoke-rc.d: initscript gdm, action "reload" failed.
Completely removing GDM and reinstalling it didn't work, either.

I can't log in until I get this fixed, please help!

SOLUTION: I ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and that fixed for some reason!

---

