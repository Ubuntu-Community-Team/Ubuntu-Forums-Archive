---
title: "[SOLVED] Automatic update: Hangs on boot (starting bluetooth)"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by barkerben on 2008-08-27
Hi -

My ubuntu 8.04 has been working fine for a while now. Last night, some automatic updates came through and asked for a reboot. I shut down the PC and went to bed. This morning, when I turned the computer back on, the boot hung for about 2 minutes complaining about my dvb tuner card, then hung indefinitely on "starting bluetooth". I tried using the recovery boot option, which gets me a desktop, but the screen resolution is stuck at 800*600. Is there a way of finding out precisely what updates were installed last night, and removing them?

Cheers,

Ben

---

### Post by barkerben on 2008-08-27
Solved. Strangely, it was the video4Linux drivers causing the problem. Rebuilt them, and everything is fine again.

---

### Post by Kaibosh on 2008-08-29
Thanks for posting the answer to your original question matey.. Saved me a bit of time there, and got my system (exact same issue) fixed nice and quickly..

---

