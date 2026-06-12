---
title: "Pulseaudio playback freezes unexpectedly"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by barisurum on 2009-09-20
After a while the playback freezes and continues when I restart playing a file (mp3, ogg, wav etc.). Pulseaudio messages in messages log:

> Sep 20 17:56:33 barubuntu pulseaudio[2486]: lock-autospawn.c: Cannot access autospawn lock.
Sep 20 18:01:33 barubuntu kernel: [   79.000145] Clocksource tsc unstable (delta = -81507666 ns)
Sep 20 18:21:40 barubuntu pulseaudio[3029]: ratelimit.c: 7 events suppressed
Sep 20 18:29:50 barubuntu pulseaudio[3080]: ratelimit.c: 7 events suppressed
Sep 20 20:32:13 barubuntu pulseaudio[3624]: ratelimit.c: 7 events suppressed
Sep 20 21:10:07 barubuntu pulseaudio[3933]: pid.c: Stale PID file, overwriting.
Sep 20 21:11:04 barubuntu pulseaudio[3933]: ratelimit.c: 7 events suppressed

Does anyone have the same problem? My soundcard is an ESI Julia envy24 HTS

---

### Post by barisurum on 2009-09-21
Noone with the same problem out there?

---

### Post by Joe_Bishop on 2009-09-21
ESI Juli@

---

### Post by gnomeuser on 2009-09-21
sounds like a driver bug, ubuntu-bug kernel should collect the required information and file a bug for you.

---

### Post by barisurum on 2009-09-21
Thanks gnomeuser. ubuntu-bug kernel says package kernel doesn't exist. And in ubuntu-bug I can't select "other problem" it says you need to specify a package or PID.

---

### Post by barisurum on 2009-09-22
anyone?

---

### Post by taavikko on 2009-09-22
> **barisurum said:**
> Thanks gnomeuser. ubuntu-bug kernel says package kernel doesn't exist. And in ubuntu-bug I can't select "other problem" it says you need to specify a package or PID.

"ubuntu-bug linux" is the correct one.

---

### Post by barisurum on 2009-09-22
Thanks taavikko it works! ubuntu-bug pulseaudio works as well.

---

