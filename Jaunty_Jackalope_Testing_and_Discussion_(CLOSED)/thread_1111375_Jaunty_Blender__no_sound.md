---
title: "Jaunty Blender  no sound"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cotcot on 2009-03-30
I did a new install on separate partitions with jaunty (version 29/3/2009). As with hardy i do not get sound in blender. Other apps are fine. In hardy i could correct it as mentioned in different forum questions (adding SDL_AUDIODRIVER=alsa to /etc/environment and/or starting with -g noaudio)
Is there anybody having sound with blender on jaunty. If so what did you do to get it ?

SOLVED :  I removed all pulseaudio packages, downloaded blender from the blender site and start the executable in the blender folder with ./blender -g noaudio. I have SDL_AUDIODRIVER=alsa added in /etc/environment. 
Other sound using apps are even not blocking blender.

---

