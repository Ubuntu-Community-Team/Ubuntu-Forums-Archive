---
title: "Sound not working after update"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by keevill on 2011-10-05
After an update which somehow was not completed correctly, sound has stopped working.
If I make a new profile, then it works.
How can I get the sound working again in my original profile ?
Ubuntu 10.04 32Bit 
Thx,
-keevill-

---

### Post by Toz on 2011-10-11
You could try resetting pulseaudio:
```
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
(ignore any errors about missing files)

Log out and back in again.

---

