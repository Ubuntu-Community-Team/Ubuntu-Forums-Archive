---
title: "3d performance in games"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Naatan on 2010-03-21
Hi guys,

I have a weird problem playing games on Lucid, I play both native linux games (quake 3 live) and games over wine (team fortress 2), but when I have Ubuntu running for a while (during which time I usually browse the web, watch youtube and work on programming projects) and then launch a game the performance is extremely bad. I end up having to quit the game, restart my computer and then it runs fine.

But again, when I do my browsing and programming for a while and THEN launch the game, it's just -bad-.

Note that when I launch the game I do close any and all open programs. I also check my process list and I see no processes taking a lot of CPU or memory.

Anyone know what I can do?

I have an Nvidia Geforce 9600 pro with the latest available proprietary driver.

---

### Post by Naatan on 2010-03-21
Also worth noting, I also play WoW but this game seems to always run smooth no matter what..

Possibly a 3D issue? I know WoW runs on OpenGL.. not sure what the other games use..

---

### Post by Naatan on 2010-03-21
I just tried running TF2 under OpenGL, still same issue.. though it seems less glitchy ..

---

### Post by Anduu on 2010-03-21
Well I don't know about other games(haven't had time to test anything yet...)however I do notice that QuakeLive performs quite poorly compared to the way it did in Karmic.

Do you have desktop effects disabled?

Also of note I am running an ATI X1300 card so it does not appear to be a driver related issue regarding QuakeLive.Perhaps a Xorg problem?

---

### Post by juancarlospaco on 2010-03-21
The devs dont say that officially but some programs/daemons run with **--debug** or **--verbose**,
its for Debugging and troubleshoting, that sends all data to logs and reports,
you can check this on gnome-system-monitor or top, intentionally packed like these,
a bug trap method i think, but maybe the reason for performance slowdown.

---

### Post by MacUntu on 2010-03-21
Quake Live running fine with nvidia-current on an old 6600GT (desktop effects disabled).

---

