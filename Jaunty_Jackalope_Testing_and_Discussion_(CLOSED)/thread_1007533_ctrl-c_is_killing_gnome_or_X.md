---
title: "ctrl-c is killing gnome or X"
date: 2008-12-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ccw on 2008-12-10
I'll Crtl-C with the intent to break out of something in a terminal window and Gnome/GDM/X restarts.

I'm thinking its GDM but don't know how to isolate it.

Has anyone else seen this? Is there a bug filed? If not what package should I file it against.

---

### Post by Kow on 2008-12-10
Well I can't reproduce it so can you check /var/log/{messages,dmesg,syslog,debug,etc} for anything that seems relevant to the ctrl+c issue and post them?

---

### Post by ccw on 2008-12-10
These seem to be timed about right...

```
Dec 10 15:49:57 chad-laptop kernel: [ 1748.837330] [drm] Num pipes: 1
Dec 10 15:49:57 chad-laptop bonobo-activation-server (chad-9588): could not associate with desktop session: Failed to connect to socket /tmp/dbus-5sA0jzQf7C: Connection refused
Dec 10 15:49:58 chad-laptop kernel: [ 1750.796882] [drm] Setting GART location based on new memory map
Dec 10 15:49:58 chad-laptop kernel: [ 1750.798850] [drm] Loading R300 Microcode
Dec 10 15:49:58 chad-laptop kernel: [ 1750.798891] [drm] Num pipes: 1
Dec 10 15:49:58 chad-laptop kernel: [ 1750.798900] [drm] writeback test succeeded in 1 usecs
Dec 10 15:50:02 chad-laptop bonobo-activation-server (chad-9643): could not associate with desktop session: Failed to connect to socket /tmp/dbus-5sA0jzQf7C: Connection refused
Dec 10 15:50:22 chad-laptop pulseaudio[10011]: pid.c: Stale PID file, overwriting.
Dec 10 15:51:00 chad-laptop kernel: [ 1811.901350] [drm] Num pipes: 1
Dec 10 15:51:02 chad-laptop kernel: [ 1813.876660] [drm] Setting GART location based on new memory map
Dec 10 15:51:02 chad-laptop kernel: [ 1813.878625] [drm] Loading R300 Microcode
Dec 10 15:51:02 chad-laptop kernel: [ 1813.878667] [drm] Num pipes: 1
Dec 10 15:51:02 chad-laptop kernel: [ 1813.878676] [drm] writeback test succeeded in 1 usecs
Dec 10 15:51:05 chad-laptop bonobo-activation-server (chad-10213): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vKPwitBtdX: Connection refused
Dec 10 15:51:06 chad-laptop kernel: [ 1818.784105] [drm] Num pipes: 1
Dec 10 15:51:11 chad-laptop kernel: [ 1822.844692] [drm] Loading R300 Microcode
Dec 10 15:51:11 chad-laptop kernel: [ 1822.844733] [drm] Num pipes: 1
Dec 10 15:51:13 chad-laptop kernel: [ 1825.008907] [drm] Num pipes: 1
Dec 10 15:51:15 chad-laptop kernel: [ 1826.948559] [drm] Setting GART location based on new memory map
Dec 10 15:51:15 chad-laptop kernel: [ 1826.950547] [drm] Loading R300 Microcode
Dec 10 15:51:15 chad-laptop kernel: [ 1826.950589] [drm] Num pipes: 1
Dec 10 15:51:15 chad-laptop kernel: [ 1826.950597] [drm] writeback test succeeded in 1 usecs
Dec 10 15:51:15 chad-laptop kernel: [ 1827.792388] [drm] Num pipes: 1
Dec 10 15:51:19 chad-laptop kernel: [ 1831.604526] [drm] Setting GART location based on new memory map
Dec 10 15:51:19 chad-laptop kernel: [ 1831.606622] [drm] Loading R300 Microcode
Dec 10 15:51:19 chad-laptop kernel: [ 1831.606664] [drm] Num pipes: 1
Dec 10 15:51:19 chad-laptop kernel: [ 1831.606673] [drm] writeback test succeeded in 1 usecs
Dec 10 15:51:42 chad-laptop pulseaudio[10572]: pid.c: Stale PID file, overwriting.
```

---

### Post by Kow on 2008-12-10
That looks like an effect of X11 being started back up after ctrl+c (which is not directly associated with the problem.)

---

### Post by ccw on 2008-12-10
> **Kow said:**
> That looks like an effect of X11 being started back up after ctrl+c (which is not directly associated with the problem.)

Yeah, I was thinking the same thing. Nothing else stands out in /var/log/*

---

