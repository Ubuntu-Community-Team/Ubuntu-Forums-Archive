---
title: "mic muted on startup"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by garba on 2009-10-26
Anybody else getting this? I filed a bug report about this problem that's been bugging me since jaunty, it's no big deal but it's annoying...

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/453475](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/453475)

---

### Post by sonicb00m on 2009-10-27
The mic isnt the problem for me but the main sound being muted. I made a start up script that fixes it and added it to the sessions manager in gnome

#!/bin/bash

amixer -q -c 0 sset 'Master',0 100% 100% unmute

You can probably replace "Master" with "mic" or whatever it's called in your mixer.

---

