---
title: "Issues with Audio"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-10-13
Anyone having issues with audio after the latest update, it keeps emitting a loud thump - followed by a fade to the right channel which just sounds like someone shuffling away - puts the hairs on the back of my head up.

Edit: noticed these lines in the logfile

> Oct 13 17:16:49 Mesh pulseaudio[2730]: module-x11-xsmp.c: X11 session manager not running.
Oct 13 17:16:49 Mesh pulseaudio[2730]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed

---

### Post by nac.est on 2009-10-14
I've been having this for a few days, too. Very frequent loud thumps, especially before and after playing sounds (like notifications). I don't get the shuffling, though.

In the log i see a lot of these:

> karmic pulseaudio[1794]: ratelimit.c: 157 events suppressed

I don't know if it's related.

---

### Post by RebateFX on 2009-10-19
> **nac.est said:**
> I've been having this for a few days, too. Very frequent loud thumps, especially before and after playing sounds (like notifications). I don't get the shuffling, though.

In the log i see a lot of these:



I don't know if it's related.

I also have 

Oct 19 12:59:27 oberon pulseaudio[3342]: ratelimit.c: 82 events suppressed
Oct 19 12:59:44 oberon pulseaudio[3342]: ratelimit.c: 84 events suppressed
Oct 19 13:00:05 oberon pulseaudio[3342]: ratelimit.c: 102 events suppressed
Oct 19 13:06:26 oberon pulseaudio[3342]: ratelimit.c: 95 events suppressed
Oct 19 13:07:14 oberon pulseaudio[3342]: ratelimit.c: 84 events suppressed
Oct 19 13:08:22 oberon pulseaudio[3342]: ratelimit.c: 103 events suppressed
Oct 19 13:11:30 oberon pulseaudio[3342]: ratelimit.c: 90 events suppressed
Oct 19 13:11:48 oberon pulseaudio[3342]: ratelimit.c: 83 events suppressed
Oct 19 13:13:20 oberon pulseaudio[3342]: ratelimit.c: 63 events suppressed
Oct 19 13:14:44 oberon pulseaudio[3342]: ratelimit.c: 116 events suppressed
Oct 19 13:17:48 oberon pulseaudio[3342]: ratelimit.c: 84 events suppressed
Oct 19 13:18:17 oberon pulseaudio[3342]: ratelimit.c: 84 events suppressed

That get thrown up in the message log every time pidgin or skype tries to make a sound on a new message.

Before this I have sound. It just randomly disappears. Pulseaudio is still fail after all this time? :/

---

