---
title: "audio delay in alsa via pulse (worked in jaunty fails in lucid)"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wscott on 2010-04-12
I have a lucid box that I upgraded from jaunty last week.
(During the beta)

It is a fairly simple machine with Intel audio and a USB
microphone.  I have not messed with alsa or pluse config
files.

Sound generally works fine and Skype works fine on this
system.

However when running noisy alsa games like Enemy Territory Quake Wars (etqw) the sound becomes delayed by about 30 seconds.  Before I upgraded, etqw sound output worked fine.

What changed to caused the alsa->pulse sound path to stop working?  It is like some buffer was allowed to grow very large.

-Wayne

---

### Post by Truga on 2010-04-16
Having exact same problem with doom3, but the bug is rather sporadic.

Sometimes it runs fine, sometimes it starts fine, breaks after a while, and sometimes it just starts delayed by a random amount.

---

### Post by barisurum on 2010-04-20
Yeah the same problem here.. I wonder if installing esound will solve anything?

---

### Post by barisurum on 2010-04-20
Yes! YAPABUG.. (yet another pulseaudio bug). Removed it from the system via synaptic, installed esound in its place and voila! Sound is in sync again!. I can control the volume in cairo dock, it says HDA Intel instead of pulseaudio. Greetin!! :D

---

### Post by psyke83 on 2010-04-20
> **wscott said:**
> I have a lucid box that I upgraded from jaunty last week.
(During the beta)

It is a fairly simple machine with Intel audio and a USB
microphone.  I have not messed with alsa or pluse config
files.

Sound generally works fine and Skype works fine on this
system.

However when running noisy alsa games like Enemy Territory Quake Wars (etqw) the sound becomes delayed by about 30 seconds.  Before I upgraded, etqw sound output worked fine.

What changed to caused the alsa->pulse sound path to stop working?  It is like some buffer was allowed to grow very large.

-Wayne

If ETQW uses SDL for sound, then it's possible that the delay is caused by the SDL ALSA plugin.

If that's the case, I recommend that you install the package *libsdl1.2debian-pulseaudio*. This package will conflict with (and therefore ask to remove) the *libsdl1.2debian-alsa* package - that's fine.

A caution regarding other advice: removing PulseAudio may have unforeseen consequences, and I would strongly recommend against its removal. Some system components may rely on/assume that PulseAudio is present, such as the volume indicator applet. 

Additionally, ESD/Esound Daemon is a deprecated piece of software and no longer maintained (because PulseAudio and libcanberra superceded it).

From [Wikipedia]("http://en.wikipedia.org/wiki/Enlightened_Sound_Daemon"):
> ESD was maintained as part of the GNOME project, but as of April 2009,  all ESD modules in Gnome have been ported to libcanberra for event  sounds or [GStreamer]("http://en.wikipedia.org/wiki/GStreamer")/[PulseAudio]("http://en.wikipedia.org/wiki/PulseAudio")  for everything else.

---

### Post by wscott on 2010-04-20
I have libsdl1.2debian-pulseaudio since that is a included as part of the ubuntu-desktop package.

I am not really interesting in removing pulseaudio because that really isn't the point of working with a beta.  Besides it was working fine with jaunty.

The etqw game uses the OpenAL library.

I ended up switching the game to using OSS ("s_driver oss" at the game console) and then running the game using pasuspender.   Then it worked fine.  Kinda bypasses the bug, but less drastic that removing pulse completely.

-Wayne

---

### Post by psyke83 on 2010-04-20
> **wscott said:**
> I have libsdl1.2debian-pulseaudio since that is a included as part of the ubuntu-desktop package.

I am not really interesting in removing pulseaudio because that really isn't the point of working with a beta.  Besides it was working fine with jaunty.

The etqw game uses the OpenAL library.

I ended up switching the game to using OSS ("s_driver oss" at the game console) and then running the game using pasuspender.   Then it worked fine.  Kinda bypasses the bug, but less drastic that removing pulse completely.

-Wayne

Maybe try running the application with the "padsp" wrapper instead (this will translate OSS calls to the PulseAudio server).

---

### Post by barisurum on 2010-04-20
OK. Installed pulse again. It seems the opposite of psyke83's suggestion works. The problem can be solved by installing libsdl1.2-debian-alsa package and forcing sdl to use alsa output. This will remove libsdl1.2-debian-pulseaudio. No need to completely remove pulseaudio. The game runs in sync now.

[COLOR="Red"]NO WAY[/COLOR] DIDN'T WORK, SEE BELOW!

---

### Post by psyke83 on 2010-04-20
> **barisurum said:**
> OK. Installed pulse again. It seems the opposite of psyke83's suggestion works. The problem can be solved by installing libsdl1.2-debian-alsa package and forcing sdl to use alsa output. This will remove libsdl1.2-debian-pulseaudio. No need to completely remove pulseaudio. The game runs in sync now.

Crazy ;). It seems that the SDL PulseAudio plugin is buggy. Glad you god it sorted, and hopefully wscott will see the same results.

---

### Post by barisurum on 2010-04-20
> Crazy

Yes crazy indeed! Forget what I said earlier, the problem is there with libsdl1.2-debian-alsa too. At first it worked synced, but then failed.. It seems its a problem with pulse itself. Will try wscott's solution.

---

### Post by Yellow Pasque on 2010-04-20
ETQW uses OpenAL for audio: [http://en.wikipedia.org/wiki/Id_Tech_4#Sound](http://en.wikipedia.org/wiki/Id_Tech_4#Sound)
Try updating to the latest OpenAL (which has pulse fixes): [https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)

---

### Post by barisurum on 2010-04-21
> Try updating to the latest OpenAL (which has pulse fixes)

Nope. It didn't fix the problem. Its strange that other games which use openal run synced, example: assaultcube.

---

### Post by psyke83 on 2010-04-21
Please see: [http://pulseaudio.org/ticket/296](http://pulseaudio.org/ticket/296)

From the bug report, it seems that the solution is here: [http://nullkey.ath.cx/~stuff/et-sdl-sound/]("http://nullkey.ath.cx/%7Estuff/et-sdl-sound/")

NOTE: **ignore** all suggestions to set up an .asoundrc file, as it's already present in another location. Ubuntu's ALSA libraries have been patched to read the configuration in /etc/share/alsa/pulse-alsa.conf whenever a running PulseAudio server is detected.

---

### Post by barisurum on 2010-04-21
Thanks psyke83! AFAIK there's no ETQW support there..

---

### Post by psyke83 on 2010-04-21
> **barisurum said:**
> Thanks psyke83! AFAIK there's no ETQW support there..

I would imagine that ETQW is not listed simply because the description has not been updated on the site. I'm fairly confident that it will work with ETQW, considering the positive confirmation on the PulseAudio bug report (which specifically refers to ETQW).

---

### Post by barisurum on 2010-04-25
Thanks a lot!

---

