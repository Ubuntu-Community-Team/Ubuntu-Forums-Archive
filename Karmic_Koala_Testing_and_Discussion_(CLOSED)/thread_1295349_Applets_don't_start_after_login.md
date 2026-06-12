---
title: "Applets don't start after login"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by m3galo on 2009-10-19
Hi, i've just installed the last beta of Karmic, ran the update manager and reboot. But after login the sound, network manager, bluetooth and battery applet don't start. They work because I can launch them manually and there is no message error in bash. But because they don't start automatically I've no sound after login for example. I have to put it back manually.

It's not a big deal, I know it's still a beta but I was wondering how to figure what's the problem...So if someone does have an idea it would be great, thanks :)

---

### Post by NCLI on 2009-10-19
This is the first I've heard of this problem. O.o

Are you installing using a daily build or the beta iso?

---

### Post by m3galo on 2009-10-19
I used the alternate iso because the desktop iso freezed during installation. But I update each time I could ;)

I forgot my wonfig btw : Dell Latitude D830 Core 2 Duo, 2GB RAM, NVS 140M Quadro nVidia, and Intel for Wi-Fi card and sound. I never had a problem with the hardware. I put it anyway just in case ;)

---

### Post by philinux on 2009-10-19
Just try logging out then back in. I've had some applets icons missing and this has restored them. Still beta.

---

### Post by m3galo on 2009-10-19
I've even tried to reboot but it has no effects...

Is there a command or something to reinitialize applets ?

---

### Post by philinux on 2009-10-19
Reboot is not the same as logging out then back in I've found.

But try this.

```
killall gnome-panel
```

This will restart the panels.

---

### Post by m3galo on 2009-10-19
I reboot and logged out and back that's what I meant, sorry :s

Restarting panels has no effect too...

Reinstall each applet could work ? But I'm not sure with all dependances of these packages :s

---

