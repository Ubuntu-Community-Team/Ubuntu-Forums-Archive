---
title: "[SOLVED] Sound troubles in Intrepid Ibex Alpha 2"
date: 2008-07-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jmmL on 2008-07-21
I've just upgraded to IIa2 from 8.04.1. Everything looks fantastic and, as far as i know, everything but sound is working.

I've tried to play the example .oggs that come with II, and while totem shows a visualisation, no sound is coming from my speakers. I'm using a Creative X-Fi XtremeAudio as my soundcard.

Now, what makes this more interesting is that i know that, at some level, sound is working. This is because when i arrive at the login screen, i am greeted with the familiar little drum-roll. So if sound is working before i log in, why isn't it working afterwards?

I'm not very experienced at all in hunting down bugs or fixing anything in linux - but i'm very happy to help. I can mess around a fair amount in ubuntu, because i have a stable linux mint install, as well as a stable vista install. The only thing i haven't done is install any of the compiz effects or the nvidia driver, because i think they cause crashes (or at least, they did in gutsy and hardy - oddly they don't in linux mint 5).

EDIT:
Thanks to an offhand comment in [this]("http://ubuntuforums.org/showpost.php?p=5394131&postcount=5") thread, I realised it was as simple as PulseAudio setting the wrong default audio device. I have easily re-configured using System>Preferences>Sound and the testing tools available there.

Thread marked as solved!

---

### Post by psyke83 on 2008-07-21
> **jmmL said:**
> EDIT:
Thanks to an offhand comment in [this]("http://ubuntuforums.org/showpost.php?p=5394131&postcount=5") thread, I realised it was as simple as PulseAudio setting the wrong default audio device. I have easily re-configured using System>Preferences>Sound and the testing tools available there.

Thread marked as solved!

Unfortunately it seems you came to the wrong conclusion. If you set everything to "ALSA" output, it's a poor workaround. Set everything back to "Autodetect" in the Sound Preferences and follow the second option in this post: [http://ubuntuforums.org/showpost.php?p=5299675&postcount=13](http://ubuntuforums.org/showpost.php?p=5299675&postcount=13)

---

