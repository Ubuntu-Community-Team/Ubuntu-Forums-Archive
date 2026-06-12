---
title: "Installation corruption"
date: 2017-11-28
forum: Installation &amp; Upgrades
---

### Post by dankerdork on 2017-11-28
A few months ago I installed Ubuntu on my PC in place of windows, and I loved it, I used it with no trouble for weeks, but I eventually got a problem with Ubuntu crashing when firefox was open, I figured I'd just avoid Firefox for now, and fix it later, but eventually the problem spread to other applications untill eventually Ubuntu itself wouldn't boot, I figured my iso was corrupt, so went to a friend's house to use their computer, formatted my usb, and remade my Ubuntu flash, I used a different program to make it too, as I heard Linux live could be unreliable, so I used unetbootin, but I had the same results with even quicker corruption, at this point I decided I would try everything, I bought a whole bunch of new usbs I tried different versions and flavors of ubuntu, I tried different friends computers to make the flash, but all of them end up crashing and displaying common corruption errors, idk what else I can do, please tell me anything else I could try.

---

### Post by dankerdork on 2017-11-28
Sorry about the wall of text

---

### Post by ian-weisser on 2017-11-28
Since it installed properly and worked great for weeks, the .iso seems unlikely to be the problem.

Eliminate hardware problems first:
Try a [SMART test]("https://help.ubuntu.com/stable/ubuntu-help/disk-check.html") on your hard drive and [Memtest86]("https://askubuntu.com/questions/917961/have-memtest86-in-the-installation-disk-menu-along-with-try-ubuntu") on your RAM.

---

### Post by Autodave on 2017-11-28
Sounds like a hardware problem to me. Do the memtest as ian-weiseer suggested: do the longest one available. If that shows nothing, move on to the HD test.

---

