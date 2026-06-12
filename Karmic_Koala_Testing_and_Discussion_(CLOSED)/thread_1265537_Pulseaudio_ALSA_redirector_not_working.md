---
title: "Pulseaudio ALSA redirector not working"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aldursys on 2009-09-13
I'd be grateful if somebody could confirm what I think is a bug. Flash and Wine appear to be locking out the ALSA audio system completely - preventing any pulseaudio sound from getting to the devices.

This is a regression from Jaunty.

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428815](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428815)

Replication steps:

Bring up a Video on You Tube and get the sound going. Then play something via Rhythmbox, or run 'speaker-test' in a Terminal. In theory you should hear both mixed together by PulseAudio.

TIA

---

### Post by joh on 2009-09-14
I have the exact same problem on my 64bit Ubuntu Karmic system.

Have you found a workaround for it?

---

### Post by lithorus on 2009-09-14
Works fine here. Which version of flash are you using?

---

### Post by joh on 2009-09-14
I'm using "Shockwave Flash 10.0 r32", according to the browser, and the package "flashplugin-nonfree", version "10.0.32.18ubuntu1".

Seems like all alsa applications steal the alsa interface instead of going through pulseaudio.

---

### Post by lean on 2009-09-14
I can confirm this.
I manually upgraded to the 64bit plugin, and the problem disapeared.

---

### Post by psyke83 on 2009-09-14
There seems to have been a bit of a mess with the 32bit PulseAudio ALSA plugins, but it seems that it is (or will soon be) fixed.

See: [https://lists.ubuntu.com/archives/karmic-changes/2009-September/008640.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/008640.html)

---

### Post by lithorus on 2009-09-14
> **lean said:**
> I can confirm this.
I manually upgraded to the 64bit plugin, and the problem disapeared.
That was my theory too. I'm also using the 64-bit version of flash.

---

