---
title: "Startup bongos and login sound choppy after upgrade"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aikon- on 2009-10-25
Yesterday I upgraded my desktop to Karmic RC (from 9.04). The bongos that play on startup (when the user is ready to login) and the sound that plays when the user actually logs in are very choppy now; sometimes later parts of the sound are heard before earlier parts of it. This was working fine in 9.04.

I have two ideas, neither of which I know how to tackle:
[LIST=1]
[*]two different processes are trying to play these sounds at the same time, perhaps causing Pulse to get confused; and
[*]Pulse is given insufficient priority to effectively play audio while the system is still busy loading itself.
[/LIST]

Any advise on the above, or any other suggestions, are more than welcome.

-Aikon

---

### Post by dentaku65 on 2009-10-25
Try to wipe away your pulse cache conf
```
sudo rm -R ~/.pulse
```
and reboot your machine.

---

### Post by Aikon- on 2009-10-25
> **dentaku65 said:**
> Try to wipe away your pulse cache conf
```
sudo rm -R ~/.pulse
```
and reboot your machine.

Done; the issue persists (there was no noticeable change).

---

### Post by FuturePilot on 2009-10-25
I have the same problem on my laptop. All other sounds play just fine. Only the login sound is choppy.

---

