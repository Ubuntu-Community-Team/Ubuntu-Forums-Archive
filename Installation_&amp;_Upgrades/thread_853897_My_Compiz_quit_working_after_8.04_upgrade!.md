---
title: "My Compiz quit working after 8.04 upgrade!"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Travler on 2008-07-09
Yesterday I booted to my 7.10 version and everything was great. I had all my cool compiz effects going on...I had my 1024x780 resolution (with a choice of about 10 more resolutions). Then the updater said there is an update available...YAY...I installed it. Now I have Ubuntu version 8.04 with no Compiz and only 2 resolution choices, 800x600 and 640x480. It seems my Nvidia drivers are no good with this version of Ubuntu. I have tried to update the drivers but the more I try the more confused I get {being the Ubuntu noob that I am}. Anyone with an easy step by step guide to getting my GT8800 video card to work here would be much appreciated.

---

### Post by mikewhatever on 2008-07-09
I'd try nvidia-settings tool. If it's not installed, do so first, then run it as root and reconfigure xserver.
Another tool present in Hardy is displayconfig-gtk. Obviously, it also needs root privileges to be able to write a new xorg.

---

