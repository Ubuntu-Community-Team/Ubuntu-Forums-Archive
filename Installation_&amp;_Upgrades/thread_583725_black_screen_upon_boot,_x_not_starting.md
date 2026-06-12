---
title: "black screen upon boot, x not starting?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Cellwind929 on 2007-10-20
I'm coming from 7.04, and I installed with the live cd and what not. Install went fine, but upon reboot things go to start and then black screen. The black screen is not on the live cd, its when I'm trying to boot off the partition. I can boot into safe mode but I have absolutely no idea what to type in, and have to boot into xp, then boot back into safe mode to try things. I tried resetting X using the code i found.
```
sudo dpkg-reconfigure xserver-xorg
```
It did absolutely nothing to fix my problem. So I appreciate anythng you 

Graphics card is an ATI x1600 mobility card in a laptop

EDIT: I'm special, I just found the answer in the release notes

So I tried editing the xorg.conf through the recovery console using this command to add in the line it suggests
```
cd /etc/x11/
then: gedit xorg.conf &
```

It claims that I cannot edit the display. The documentation on how to actually edit the file to fix it is poorly documented anywhere. I'm going back to 7.04, or saying screw ubuntu all together.

---

