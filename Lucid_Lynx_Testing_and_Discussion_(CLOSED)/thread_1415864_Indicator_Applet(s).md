---
title: "Indicator Applet(s)"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by johoe on 2010-02-25
Basically I like the new indicator applets idea - but I've one big problem with it:
I've a dark wallpaper and transparent gnome panels. So I can't (hardly) see the indicators icons/text.

Is there a way to change the "theme" of this indicators?

johoe

---

### Post by philinux on 2010-02-25
Try the humanity-dark icons.

---

### Post by LKjell on 2010-02-25
> **johoe said:**
> Basically I like the new indicator applets idea - but I've one big problem with it:
I've a dark wallpaper and transparent gnome panels. So I can't (hardly) see the indicators icons/text.

Is there a way to change the "theme" of this indicators?

johoe

There is a big flaw with the indicator applet... If you do not have it on it should give you the normal applets. Right now I do not have some applets since I do not use gnome-panel thus cannot add the indicator applet.

---

### Post by castrojo on 2010-02-25
> **LKjell said:**
> Right now I do not have some applets since I do not use gnome-panel thus cannot add the indicator applet.

If an application you are using isn't falling back then that's a bug, app indicators have a fallback mechanism to give you the icon in the old notification area if it detects that indicator-application-service isn't running.

So rhythmbox, transmission, etc. should all be working. If an application isn't working please file a bug and tag it with "indicator-application".

I don't think the messaging-indicator itself (the envelope) will work in the old area though so you might be out of luck there.

---

### Post by johoe on 2010-02-26
I see, it just would have been nice, when the indicator applet were using the defined colours in .gtkrc-2.0.

gnome-panel is probably dying anyway with the appearance of gnome-shell. So this might be no issue for the future...

johoe

---

