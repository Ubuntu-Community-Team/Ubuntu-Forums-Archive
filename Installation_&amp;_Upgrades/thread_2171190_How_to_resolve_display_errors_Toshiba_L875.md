---
title: "How to resolve display errors Toshiba L875?"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by dean7 on 2013-08-29
I have a Toshiba L875, AMD, with Radeon graphics card. Win8 was pre-installed. There are two problems but I believe one underlying cause.


Ubuntu 13.04, 64-bit, is installed. Based on the one thread i've found here, i don't know if the problem is solvable. am going to try anyway.


**Problem**: the first is that the display has random gray artifacts. Grey boxes or what look like grey shards of broken glass, randomly appear on screen. Triggering a refresh (resize or move a window) usually removes the artifacts, though they reappear.


**How I've tried to fix it:**


 1. Have verified that open source Radeon drivers are in use (Settings > Software & Updates > Additional drivers)
 2. Have added proprietary ATI drivers (same as above)
 3. Have added ATI catalyst center
 4. Added latest kernel, 3.10
 5. Installed various distros: Mint, Ubuntu 13.04, 12.04 LTS, Lubuntu,  different desktops (I was trying to omit `compiz`; I thought `compiz` was in Ubuntu only).
 6. Removed `compiz`. That was a mistake :)


Each of these attempts are separate, not cumulative. 


Adding/changing drivers either had no effect on the problem or, in the case of the proprietary drivers, I had to reinstall Ubuntu, as a reboot ended with a black screen and blinking white cursor that accepted no commands.


I attempted to remove/change `compiz` because most Ubuntu reported errors listed `/usr/bin/compiz` as the location.


**Problem 2:** Oh, and my ultimate goal is to get dual monitors working. Any attempts to plug-in a VGA monitor blank the laptop monitor or freeze it.


**Currently**: my attempts are more whack-a-mole than systematic and probably incorrect in some way, but I am not sure what else to do: it seems a video problem. 


A fresh install awaits at home, so the changed video drivers and kernel are no longer in-play.


However, I believe what fixes one problem will fix the other.


I've learned a lot over the 25 or so hours spent researching and trying to resolve the video problem, but I need it to work now. Before I jumped, I used a VM for about a month and set-up a Bitnami WordPress stack as a very good OneNote replacement. So, I checked workflow. And, I could be wrong, but was sure dual monitors worked when I ran the LiveDVD to test for hardware support. Anyway, like the Ham & Egg breakfast story that explains the difference between involved and committed (the chicken is involved, the pig committed), I removed Win 8 and went all-in. So, I am committed.


Thanks for any support, I appreciate the time of those in the forum.

---

