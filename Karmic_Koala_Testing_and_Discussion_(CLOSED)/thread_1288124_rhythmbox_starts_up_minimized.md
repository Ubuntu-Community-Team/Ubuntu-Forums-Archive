---
title: "rhythmbox starts up minimized"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-10-11
I'm figuring this is a karmic problem as I don't have it in jaunty. When I start up Rhythmbox it always starts up minimized. Is there a setting or something I can't find or is this a peculiarity to karmic?

Thanks!

---

### Post by VMC on 2009-10-11
gconf-editor:
 [FONT="Courier New"]/ apps > rhythmbox > plugins > status-icon[/FONT]. Then check [FONT="Courier New"]window-visible[/FONT]

---

### Post by oboedad55 on 2009-10-11
> **VMC said:**
> gconf-editor:
 [FONT="Courier New"]/ apps > rhythmbox > plugins > status-icon[/FONT]. Then check [FONT="Courier New"]window-visible[/FONT]

Got it. I just had to clear the check-box. Thanks, I figured it was something mindless like that.

---

