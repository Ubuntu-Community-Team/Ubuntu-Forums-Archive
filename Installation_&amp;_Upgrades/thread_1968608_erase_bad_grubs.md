---
title: "erase bad grubs"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2012-04-29
i have a bad upgrade to 12.04 that had unuseable desktop so when i rebooted when the grub screen came up i chose the third line down that was labeled 'use previous version'.When i clicked that option another list of grub numbers appeared so i randomly chose the second one down figureing i would be back to 11.10 but when i booted that one it started a boot of 12.04 that works perfectly.I am afraid to turn off computer now in case i cant remember what grub im using now.Is there a way to display current grub version and trash all others?.

---

### Post by dino99 on 2012-04-29
its not several grub, but an organized grub menu with submenu. If you want to tweak that order, its easy with grub-customizer (find it in launchpad ppa). There you can move the lines, define the appearance etc.

---

### Post by jesse c on 2012-04-29
thanks dino99 .not intuitive for novice but somehow i did it thru terminal.I couldnt follow anything on the new desktop GUI

---

### Post by dino99 on 2012-04-29
> **jesse c said:**
> thanks dino99 .not intuitive for novice but somehow i did it thru terminal.I couldnt follow anything on the new desktop GUI

if you want the old feel & look, then install gnome-session-fallback, alacarte, synaptic; then login as gnome-classic

---

