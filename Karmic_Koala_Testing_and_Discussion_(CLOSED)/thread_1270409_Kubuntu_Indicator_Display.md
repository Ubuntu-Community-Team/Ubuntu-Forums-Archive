---
title: "Kubuntu Indicator Display"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-09-19
There used to be an indicator display, which looked like a little envelope icon near the sys tray. It's gone now and replaced with a red x. I checked kpackagekit and it is still installed, so has the icon been deprecated, or should I report this as a bug?

Edit: I don't even know what the icon did in the first place...

---

### Post by ilna on 2009-09-19
Also am finding it... Have tried to reinstall plasma-widget-indicatordisplay without any success.

---

### Post by nystire on 2009-09-20
Is it starting at all? That sounds like the applet isn't starting, so the display part is throwing the error due to it not being able to connect to the applet.

---

### Post by jlacroix on 2009-09-20
> **nystire said:**
> Is it starting at all? That sounds like the applet isn't starting, so the display part is throwing the error due to it not being able to connect to the applet.

How do I find that out? Also, doesn't KDE 4.3 have an indicator built in? Part of my confusion is that I don't even know what the thing does...

---

### Post by Seren on 2009-09-20
> **jlacroix said:**
> How do I find that out? Also, doesn't KDE 4.3 have an indicator built in? Part of my confusion is that I don't even know what the thing does...

There is a whole blog post dediacted to notification and indicators, here :

[http://agateau.wordpress.com/2009/09/18/indicators-notifications-and-co/](http://agateau.wordpress.com/2009/09/18/indicators-notifications-and-co/)

Basically, the indicator applet is here to "store" notifications while you are away.

A notification will only be there for a few seconds, if you are not in front of the keyboard it is easily missed.

As far as I inderstand, "indicator" is a kubuntu specific development, while systray notifications are part of KDE.

---

### Post by jlacroix on 2009-09-20
> **Seren said:**
> There is a whole blog post dediacted to notification and indicators, here :

[http://agateau.wordpress.com/2009/09/18/indicators-notifications-and-co/](http://agateau.wordpress.com/2009/09/18/indicators-notifications-and-co/)

Basically, the indicator applet is here to "store" notifications while you are away.

A notification will only be there for a few seconds, if you are not in front of the keyboard it is easily missed.

As far as I inderstand, "indicator" is a kubuntu specific development, while systray notifications are part of KDE.

Thank you for the information, now I understand it. I think I'll just ignore this for now, because I do not want two notification areas on my desktop...

---

### Post by ilna on 2009-09-22
plasma-widget-indicatordisplay was updated and available again. But it shows nothing (nor KMail, nor Kopete new messages are reflected) except for white dead envelope.

Is it for me only?

---

