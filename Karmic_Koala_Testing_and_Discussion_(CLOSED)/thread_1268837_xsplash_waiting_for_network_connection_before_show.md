---
title: "xsplash waiting for network connection before showing desktop..."
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Taoye on 2009-09-17
Is this supposed to happen? I installed Alpha 5 and everything was fine. After running an apt-get upgrade yesterday evening, when booting up, the xsplash splash screen appears to be waiting for my network connection to resolve. When I remove xsplash, Gnome loads up to a working desktop in a few seconds and then, sure enough, network manager is still sitting there swirling around for a good 10 seconds before it connects to my wireless network.

Is xsplash actually waiting for my network connection? Is it supposed to do this?

---

### Post by VMC on 2009-09-17
> **Taoye said:**
> Is this supposed to happen? I installed Alpha 5 and everything was fine. After running an apt-get upgrade yesterday evening, when booting up, the xsplash splash screen appears to be waiting for my network connection to resolve. When I remove xsplash, Gnome loads up to a working desktop in a few seconds and then, sure enough, network manager is still sitting there swirling around for a good 10 seconds before it connects to my wireless network.

Is xsplash actually waiting for my network connection? Is it supposed to do this?

Did you actually uninstall package xsplash, or remove splash from kernel stanza?

---

### Post by glasen on 2009-09-17
I have the same problem with my two notebooks :

If "xsplash" is installed, loading GNOME is about 10s longer than without "xsplash". I've completely deinstalled "usplash" and removed the "splash"-option from the file "menu.lst"

---

### Post by NCLI on 2009-09-17
I doubt this is how it's meant to work. It should be resolved soon.

---

### Post by MacUntu on 2009-09-17
AFAIK it should stop once nautilus and the panel are running but right now this doesn't seem to work. Don't worry, I'm sure we'll see a fix soon.

---

### Post by Taoye on 2009-09-18
I actually uninstalled it.

OK cool... guess I'll just leave it uninstalled for now :D

---

### Post by VMC on 2009-09-18
> **Taoye said:**
> I actually uninstalled it.

OK cool... guess I'll just leave it uninstalled for now :D

Yes, I never thought of doing that, but I did it anyway and it is much faster boot up.

---

### Post by MacUntu on 2009-09-21
Signal thingy working, no delay anymore. :)

---

