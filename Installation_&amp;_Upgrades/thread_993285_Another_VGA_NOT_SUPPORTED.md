---
title: "Another VGA NOT SUPPORTED"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by chata on 2008-11-25
I installed Ubuntu 8.10 with many problems (had to do alternate install with text view) into my older Dell PowerEdge 2800 (Intel Xeo Processor/Video Embedder AI Radeon).

When it finishes booting up I get the error message:
MESSAGE
VGA MODE NOT SUPPORT
H: 74.9 KHz 
V: 60.0 Hz

I searched google and these forums and did what was most suggested (after pressing Ctrl/Alt/F1 to get the console):
sudo dpkg-reconfigure -phigh xserver-xorg
and many variations of that and all I get is how to re-set my keyboard, nothing about imputing specific VGA.

I do get these errors at bootup too:
kinit: trying to resume image from /dev/sda5
kinit: no resume image, doing normal boot
and can't get through to the internet to download compiz-check.

Sounds awful? I probably need to re-install, but with the VGA problems it would be the same alternate/txt version install.

Any suggestions?  **cries**

---

### Post by Pumalite on 2008-11-25
Did you try Recovery Mode>'xfix'?

---

### Post by chata on 2008-11-25
> **Pumalite said:**
> Did you try Recovery Mode>'xfix'?


Yea, it didn't work.

---

