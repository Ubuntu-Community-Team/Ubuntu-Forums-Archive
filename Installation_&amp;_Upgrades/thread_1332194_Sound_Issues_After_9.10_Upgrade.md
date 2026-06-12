---
title: "Sound Issues After 9.10 Upgrade"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by ricree on 2009-11-20
After the upgrade, some applications have a very bad echoing effect whenever I try to play any sounds.  However, other programs seem to work fine.

In particular, Rhythmbox and Banshee both experience this problem.  

VLC and flash video seem to be working absolutely fine.


Since it's so program specific, my best guess is that there's a library problem somewhere, but I'm not sure how to track it down and fix it.

Any suggestions?

---

### Post by ricree on 2009-11-20
Fixed thanks to Kostkon on #ubuntu and thaytan on #gstreamer.

Gstreamer was set to use OSS because of some issues I had getting sound to work in 9.04.  However, OSS was choppy in this version and pulseaudio now works fine.

The problem was, gstreamer-properties doesn't set all the necessary keys.  In particular, the key musicaudiosink under gstreamer>0.10>audio>default in gconf was not updated.  Changing it from osssink to pulsesink fixed the sound issue.

---

