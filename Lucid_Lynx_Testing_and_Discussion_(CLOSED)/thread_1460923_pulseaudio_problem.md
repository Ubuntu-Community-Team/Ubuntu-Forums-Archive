---
title: "pulseaudio problem"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-04-23
Just rebooted my newly installed RC and Pulseaudio seems to have a problem. My audio device is missing in the sound prefences.

Haven't had a single pulseaudio issue for about a year so this is a bit of a nasty and unwelcome surprise.

I think i have some intel onboard sound chip (something generic, ICH something).

---

### Post by sonicb00m on 2010-04-24
[http://e-mats.org/2010/01/missing-devices-or-sound-card-in-pulse-audio/](http://e-mats.org/2010/01/missing-devices-or-sound-card-in-pulse-audio/)

seemed to help

---

### Post by dino99 on 2010-04-24
> **sonicb00m said:**
> Just rebooted my newly installed RC and Pulseaudio seems to have a problem. My audio device is missing in the sound prefences.

Haven't had a single pulseaudio issue for about a year so this is a bit of a nasty and unwelcome surprise.

I think i have some intel onboard sound chip (something generic, ICH something).

install gnome-alsamixer and tweak settings

---

### Post by sonicb00m on 2010-04-24
why would i want gnome-alsamixer?

---

### Post by dino99 on 2010-04-24
[http://ubuntuforums.org/showthread.php?t=1461260](http://ubuntuforums.org/showthread.php?t=1461260)

---

### Post by sonicb00m on 2010-04-24
Ok well I had already fixed it reinstalling pulse.

I've not needed to check alsa-mixer for mute since around 9.04 as pulse has worked flawlessly since 9.10.

---

