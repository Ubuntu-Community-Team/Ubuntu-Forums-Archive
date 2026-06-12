---
title: "wine+pulseaudio = freeze"
date: 2010-01-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-01-19
since a week or so, wine 1.1.36 + pulseaudio (0.9.22~ *) come in general freeze:
~ 80% cpu
~ gnome-setting-daemon crash randomly due to "not enough memory" on a system with q9550 + 4go.

Have to remove ubuntu-desktop & purge all pulseaudio packages to have a stable system.

Is anyone else having such trouble ?

---

### Post by kostkon on 2010-01-19
First of all, it's an alpha release and you expect such things to happen. Secondly, instead of removing PulseAudio (and thus defeating the purpose of running Lynx, which is for testing reasons and PulseAudio comes by default in Ubuntu), why not first check your sound preferences in winecfg.
> ~ gnome-setting-daemon crash randomly due to "not enough memory" on a system with q9550 + 4go.
I'm not sure whether this is related to the pulseaudio problem.

---

### Post by dino99 on 2010-01-20
> **kostkon said:**
> First of all, it's an alpha release and you expect such things to happen. Secondly, instead of removing PulseAudio (and thus defeating the purpose of running Lynx, which is for testing reasons and PulseAudio comes by default in Ubuntu), why not first check your sound preferences in winecfg.

I'm not sure whether this is related to the pulseaudio problem.

Actual wine is very stable & this problem only appear with the last Lucid updates few days ago. Of course, when wine is updated , winecfg is updated too each time. Looking at system-monitor: pulseaudio and gnome-setting-daemon have a too heavy cpu activity and that freeze an application and slow down all the system.

As logs don't show errors about that, i even don't know exactly what package or dependency create this problem: even when it complaint about missing memory, system-monitor still show lot of free memory not used.

So, is system-monitor showing wrong information ?

note: this problem is not only with Lucid, it's the same with Karmic.

---

### Post by dino99 on 2010-01-20
ok , got it

after removing/purging then reinstalling alsa/pulseaudio, i still have the same problem. Configuring sound device & output doesn't help.
But i have seen some mixed devices: digital & analog ( i only have analog).

So, i have deleted the hidden files : .pulse & .gstream*, then reboot.

Bingo, sound is perfect now.  :P

---

### Post by dino99 on 2010-01-20
unfortunately, after installing last kernel and rebooting, the problem is back.

There is something wrong with alsa/pulseaudio configuration. I have sound but for a while, about 10 mn, cpu is heavyly charged. Then memory seem to be freezed: when i check a menu and close it, the frame does not disappear and the mouse is hidden on the active window.

---

### Post by dino99 on 2010-01-20
can't use metatrader with wine due to this alsa problem:

alsa plug-in [wine preloader] freeze wine and hide mouse on active windows: huge cpu activity on pulseaudio and gnome-setting-daemon.

Googling around, some users says to deselect alsa and choose esound instead, what i have done in winecfg, then kill pulseaudio.
Wine work better but is very slow with this sound choice. Choising esound or oss does not help much.

Removing/purging alsa/pulseaudio then reinstall them does not work, erasing .pulse neither, nothing special in logs.

This is test on Lucid with wine 1.1.36 that was well working 2 weeks ago before last alsa upgrades.

---

### Post by cariboo on 2010-01-20
Bug #?

---

### Post by dino99 on 2010-01-21
devs says they have fixed pulseaudio and still work on alsa, and i really don't know what package to report against.

i've removed pulseaudio for the moment, and fill my comments on launchpad report (both alsa & pulseaudio & wine).

---

