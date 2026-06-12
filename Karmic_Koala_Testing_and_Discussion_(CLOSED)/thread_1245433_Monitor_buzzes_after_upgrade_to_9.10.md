---
title: "Monitor buzzes after upgrade to 9.10"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by slymi2005 on 2009-08-20
So I just upgraded to 9.10 and now I keep hearing a buzzing noise from my monitor, it might be the speakers because when I hit mute or play something it goes away but then when I stop it comes back in a few seconds. Is anyone else having this problem or does anyone have any suggestions on how to fix it. I noticed that the Sounds application under Preferences is different from 9.04 so not sure if something needs to be changed there.

---

### Post by dinxter on 2009-08-20
might be a bug in sink suspension when its idle, you could try looking in /etc/pulse/default.pa and commenting out the line,

load-module module-suspend-on-idle

if this cures it you should file a bug on pulseaudio about it, if there isnt one already

---

