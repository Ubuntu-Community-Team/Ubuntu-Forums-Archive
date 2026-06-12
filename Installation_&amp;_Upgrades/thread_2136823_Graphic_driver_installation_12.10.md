---
title: "Graphic driver installation 12.10"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by axept on 2013-04-18
Hello, first thing, my "enter" doesn't work in this forum, so sorry.. I have a Fujitsu Lifebook a532 With the i7 inside. This have 2 different GPU's. The Integrated HD4000 and Geforce 620/630M. In System Info it's listed as "Unknown" and "Standard". Searched the web (for many hours) and solution was: install linux-headers-generic and then the nvidia drivers. So I did... With the result of low resolution and just the wallpaper. Couldn't change resolution becasue there was no other to choose. Purged the nvidia drivers, and was back to Unity, but same resolution and couldn't change. Tried the nvidia-current-updates, With same results. Gave up, purged them and now I only get a black screen. Whats wrong? Both GPU's shows when "lspci -v". Anyone that can help? There's not possible to install from "additional Drivers" because there isn't listed anything there....:confused:

---

### Post by QIII on 2013-04-18
Hello!

You have an NVidia/Intel hybrid system ("Optimus").  The OEMs have not provided great support to the Linux community for Optimus or ATI/Intel hybrids.

The first place I would look is [here](https://help.ubuntu.com/community/HybridGraphics).

If there is not enough information, you can use the search tool above.  Just type in "Optimus" and you will get a lot of results.

This issue is causing problems all across the Linux landscape, not just Ubuntu.

Sorry I don't have a simple answer or better news.

Best wishes!

---

