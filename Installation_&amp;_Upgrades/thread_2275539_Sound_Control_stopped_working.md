---
title: "Sound Control stopped working"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by peyre on 2015-04-26
Hey, I just upgraded from Xubuntu 14.10 to 15.04, and the volume controls on my keyboard no longer work.

In previous versions, I set two keyboard shortcuts to do
pactl set-sink-volume 0 -- -5% and
pactl set-sink-volume 0 -- +5%

and I could quickly and easily control my system volume from the keyboard.  Thank you *buntu!  But now I've upgraded to 15.04, those keys no longer work.  They don't echo on the screen like they used to (it would show a notification when I hit up/down volume) and they don't raise and lower the volume.  Is there a change in syntax I need to use, or maybe a whole new command?

---

### Post by peyre on 2015-04-27
Ah ok, fixed it.  It does seem to be a change of syntax.  I took out the "--" so now the commands are:

pactl set-sink-volume 0 -5% and
pactl set-sink-volume 0 +5%

just in case anyone else experienced this.

---

