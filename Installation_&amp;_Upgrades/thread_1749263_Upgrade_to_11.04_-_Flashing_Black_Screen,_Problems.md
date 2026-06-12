---
title: "Upgrade to 11.04 - Flashing Black Screen, Problems with Unity Compatibility?"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by CyberPrime on 2011-05-04
So I tried updating from 10.10 to 11.04 yesterday, and I rebooted today to the new Grub 1.99 (very nice). That worked fine, so I hit enter to proceed to booting into 11.04. It went on it's way, seeming like it was doing fine, but then my screen started to flash. It alternated between black and blank terminal, and did so rather quickly a few times. Then it went to the verbose terminal which showed a virtualbox kernel error. I uninstalled virtualbox in the recovery mode, and restarted. Same thing, but this time without the error. I've tried repairing broken packages and booting into safe graphics mode, but I can't figure out the problem.
I then tried to boot into the previous kernel version, only to get a mouse and nothing else. I hear the startup sound, but I don't see anything (my mouse also changes to the text highlighter in certain areas). I tried clicking around a bit but nothing. I can, however, boot into the safe graphics mode of that kernel, which I'm in now. It tells me I don't have the proper hardware to run unity, then boots me into normal gnome (in low graphics mode).

Anybody have any ideas? Should I just wait for an update? Should I do a fresh install (I don't have anything on there that I really will miss)?

---

### Post by CyberPrime on 2011-05-04
Solved it! I had to remove my ATI restricted drivers. Works now!

---

