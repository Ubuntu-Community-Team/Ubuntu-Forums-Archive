---
title: "Sound Does Not Work Properly"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by titus on 2005-04-13
Hi, with esd I have delayed sound in all media players (totem / xine / mplayer). 

How can I remove esd and replace with alsa?

Any potential problems i might encounter?

Thanks,

Titus.

---

### Post by titus on 2005-04-13
killall esd, followed by alsa in whichever app works okay, but i'd like something I don't need to interfere with.

:p

---

### Post by Dr Gonzo on 2005-04-13
You can't replace esd with ALSA, as ALSA is what esd runs on top of.

You can set up esd to only spawn when an application asks for it.  There's a similar post on this forum right now where I show how to do this.  Alternatively, look [here on the Wiki](http://www.ubuntulinux.org/wiki/RestrictedFormats) for information on how to do this.

---

