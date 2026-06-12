---
title: "HELP: Ubuntu won't load GUI after Alsa re-install"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by omidomid on 2008-03-25
I was having issues with my sound in Gutsy for about a month now, so I decided to try to fix it. I re-installed the newest alsa drivers and rebooted. When the login screen was supposed to come on, it says it failed to load the image and leaves me at a terminal-like state with no GUI. If I try to run Xorg or cntrl+alt+backspace, it takes me to a black and white spotted blank desktop with an X for the cursor. Can anyone help???

---

### Post by omidomid on 2008-03-25
Problem fixed. A friend of mine told me to run 
```
sudo apt-get install gdm
```
Don't know how this got removed but it's fixed now.

---

