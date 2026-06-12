---
title: "Function Keys [Fn] on Fujitsu-Siemens Amilo Pi 2530 not working"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Bumerang on 2011-04-21
Function Keys [Fn] on Fujitsu-Siemens Amilo Pi 2530 not working

I've installed Ubuntu 10.10 on a Fujitsu-Siemens Amilo Pi 2530 laptop. The problem is that the Function keys(FN) are not working properly. When i use FN+F3 for example, which is the shortcut for sound mute the whole keyboard freezes. I've tried to set my keyboard shortcuts using System - Preferences - Keyboard Shortcuts but after that its the same, when i input a shortcut for a specific function the keyboard freezes again. Someone? :)

---

### Post by maik3l on 2011-05-05
Same with me - I'm running Fujitsu-Siemens Amilo Pi 2550 with Xubuntu 11.04. All other function keys (like dimming or brightening the display) seem to work perfectly fine, but volume up and down as well as mute functions not only don't work at all, but most importantly cause keyboard to become irresponsive. Also, it made session menu panel button not to response to mouse click, which left me no other seemingly feasible choice but to change TTY with alt+ctrl+Fsomething and use "kill -9 -1".
The exact behavior for aforementioned function keys looks like this: for volume up and down, single hit makes volume change a single unit up or down, and after a while volume continues to go all the way up or down. For mute function, it makes volume to mute and unmute alternately very fast, disco style. So I infer that single hit on those buttons are interpreted as them being held all time, which would also explain why the keyboard dies.
It's a long time since I've been using ubuntu so I don't really know if it's a bug or if I just lack some application and that's why I didn't hit the bugtracker yet...

---

### Post by marfalkov on 2011-06-03
Ubuntu 11.04
FS Amilo Pi2530

same here, at least i've killed the unity... :)

---

