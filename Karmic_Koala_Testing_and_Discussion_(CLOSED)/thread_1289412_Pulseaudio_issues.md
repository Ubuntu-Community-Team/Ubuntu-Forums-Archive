---
title: "Pulseaudio issues?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Grimhound on 2009-10-12
Okay, I'm going to list some issues I've had with audio on my Compaq Presario C712nr notebook in the hopes of figuring them out.

#1: When audio is not actively playing, the electronic transmissions from the motherboard play through the speakers. (Older issue, have experienced on different computers back in the 6.xx era, IIRC)

#2: Audio lags when becoming active, taking ~1 second to start when sound is transmitted to the speakers when previously there was none. Audio seems to fall into an idle state which is likely a normal feature, yet recovery from the idle state is the main issue.

---

### Post by Anubis on 2009-10-12
> **Grimhound said:**
> Okay, I'm going to list some issues I've had with audio on my Compaq Presario C712nr notebook in the hopes of figuring them out.

#1: When audio is not actively playing, the electronic transmissions from the motherboard play through the speakers. (Older issue, have experienced on different computers back in the 6.xx era, IIRC)

#2: Audio lags when becoming active, taking ~1 second to start when sound is transmitted to the speakers when previously there was none. Audio seems to fall into an idle state which is likely a normal feature, yet recovery from the idle state is the main issue.

#1 Is annoying isn't it? But I can only hear it with headphones on. I doubt they EVER fix that though.:confused:

---

### Post by MALEADt on 2009-10-12
> **Grimhound said:**
> Okay, I'm going to list some issues I've had with audio on my Compaq Presario C712nr notebook in the hopes of figuring them out.

#1: When audio is not actively playing, the electronic transmissions from the motherboard play through the speakers. (Older issue, have experienced on different computers back in the 6.xx era, IIRC)

#2: Audio lags when becoming active, taking ~1 second to start when sound is transmitted to the speakers when previously there was none. Audio seems to fall into an idle state which is likely a normal feature, yet recovery from the idle state is the main issue.

Both might be a consequence of PA's new behaviour: to lower power usage, PA now goes idle after ~2sec. Some drivers aren't perfect though, it might be that yours produces some noise when idle, the driver on my laptop's audio chipset crackles a bit when going into idle mode.
[quote=Lennart Poettering by LWN]There were a number of issues with the current sound drivers that Poettering listed as needing attention in the coming year. Currently, for power saving purposes, PulseAudio shuts down devices two seconds after they become idle. That can lead to problems with drivers that make noise when they are opened or closed.[/quote]

---

### Post by jmmL on 2009-10-12
> **MALEADt said:**
> Both might be a consequence of PA's new behaviour: to lower power usage, PA now goes idle after ~2sec. Some drivers aren't perfect though, it might be that yours produces some noise when idle, the driver on my laptop's audio chipset crackles a bit when going into idle mode.

I've got this problem - it's infuriating. I can put up with a "pop" or "crackle" going in and/or out of sleep mode, but since the recent updates (within 24 hours I think) something has been waking pulseaudio up every 30s or so, causing annoying crackles in the process. My work around currently is to play music very, very quietly - thereby stopping pulseaudio from sleeping.

---

