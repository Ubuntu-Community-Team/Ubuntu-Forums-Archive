---
title: "[ESD] unable to open slave"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by Dracontopes on 2005-04-24
I'm trying to get multiple sounds to work on my soundcard, Soundstorm (nVidia nForce 2 onboard sound). 

I have installed the libesd-alsa0 package, made a asound.conf file etc etc, everything from the guide. 

Now, I had ESD disabled, but I need it running for ESD to use ALSA so I can hear multiple sounds from different applications at the same time. 

ESD has trouble starting:

```

chris@chris:~ $ esd
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
chris@chris:~ $

```

What the...

---

### Post by Dracontopes on 2005-04-25
Damn, this thread is on the second page already and no replies yet!

Anyone?

---

### Post by student on 2005-04-25
I had the same problem,
you probably made the asound.conf file like it's explained here and there.
The problem is they tell you what to do, without explaining WHAT you do.
Since you have only one soundcard, you dont have a slave (like me).
I solved it by pointing the slave back to the the master.

pcm.!default {
type plug
slave.pcm "pcm.card0"
}


This solves the error, and esd will start.
But for myself, I still dont hear sound while the volume monitor does show sound playing.
My diagnosis is that ubuntu sees the audio capture device of my terrarec tv-card as my soundcard, but i have an intel ac'97 onboard.

And NO ! i'm not gonna buy an soundblaster live card.

---

### Post by Dracontopes on 2005-04-25
Thank you! That did the trick. Hopefully this thread will be useful for everybody with the same problem we had. ;)

---

