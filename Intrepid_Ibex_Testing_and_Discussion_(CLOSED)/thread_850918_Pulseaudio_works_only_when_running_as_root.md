---
title: "Pulseaudio works only when running as root"
date: 2008-07-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Timon&amp;Pumba on 2008-07-06
Hi, I have been messing around with the pulseaudio and alsa configuration (because it did not work). I took the various hints laying around on the internet in advice.

Conclusion: it works, but only when running it as root. Running a system wide daemon also works, but that is not recommended and a game (ET with SDL) I like to play does fail on that.
So I like to run it as a session-daemon as it supposed to do. But then I do not get sound. Running pulseaudio in a terminal as root works fine.
I checked if I do not have user-specific config files that could screw me (.asoundrc .pulse).

Can anyone point me in the direction what to try next?

---

### Post by kostkon on 2008-07-06
> **Timon&Pumba said:**
> Hi, I have been messing around with the pulseaudio and alsa configuration (because it did not work). I took the various hints laying around on the internet in advice.

Conclusion: it works, but only when running it as root. Running a system wide daemon also works, but that is not recommended and a game (ET with SDL) I like to play does fail on that.
So I like to run it as a session-daemon as it supposed to do. But then I do not get sound. Running pulseaudio in a terminal as root works fine.
I checked if I do not have user-specific config files that could screw me (.asoundrc .pulse).

Can anyone point me in the direction what to try next?
Make yourself a member of *pulse*, *pulse-access* and *pulse-rt* groups and see if this solves your problem.

---

### Post by Timon&amp;Pumba on 2008-07-06
> **kostkon said:**
> Make yourself a member of *pulse*, *pulse-access* and *pulse-rt* groups and see if this solves your problem.

I had not checked that yet, but this was already the case, so this is not the solution.
Thanks anyway.

Additionally:
Running pulseaudio as root works, but then executing enemy territory with sdl support gives this:
```

------- sound initialization -------
SDL audio driver initializing...
*** PULSEAUDIO: Unable to connect: Connection refused
SDL_AudioDriverName() = NULL
------------------------------------
Sound memory manager started

```

---

### Post by kostkon on 2008-07-06
> **Timon&Pumba said:**
> I had not checked that yet, but this was already the case, so this is not the solution.
Thanks anyway.

Additionally:
Running pulseaudio as root works, but then executing enemy territory with sdl support gives this:
```

------- sound initialization -------
SDL audio driver initializing...
*** PULSEAUDIO: Unable to connect: Connection refused
SDL_AudioDriverName() = NULL
------------------------------------
Sound memory manager started

```
Have you installed *libsdl1.2debian-pulseaudio*?

---

### Post by Timon&amp;Pumba on 2008-07-06
> **kostkon said:**
> Have you installed *libsdl1.2debian-pulseaudio*?

Yeah, that solved the problem with ET. At least the current output given seems ok:
```

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x9718780 dma buffer
No background file.
----------------------
```

But still no sound. Notice the "sound system is muted" line. I followed that lead and discovered another wierd thing that could be the main issue.

When I have pulseaudio running as session daemon, I can toggle mute/unmute on the output device in "pulseaudio volume control". **When unmuting, I hear some sound for tens of a second, but then it gets muted again.** I do not think I have muted my sound anywhere, but it seems that that is the problem. What application could be constantly overriding the pulseaudio volume control?

---

### Post by Timon&amp;Pumba on 2008-07-06
I tried the "test suite" of this page: [Pulse_Audio Testing]("http://en.wikibooks.org/wiki/Configuring_Sound_on_Linux/Pulse_Audio/Testing").
All the output of the commands look the same like on the example page.

---

### Post by plun on 2008-07-06
Just some facts....


Hobbses thread about to set the card

[http://ubuntuforums.org/showthread.php?t=845844](http://ubuntuforums.org/showthread.php?t=845844)


but we have a "full house" with bugs so this master piece
to howto give you more

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

And all facts at Pulseaudios site

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

Maybe too much of info....:)

---

