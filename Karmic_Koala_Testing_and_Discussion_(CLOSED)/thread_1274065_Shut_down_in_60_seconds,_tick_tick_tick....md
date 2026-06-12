---
title: "Shut down in 60 seconds, tick tick tick..."
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2009-09-24
Hi all
I'd like to remove the 60 seconds dialogue box when I'm shutting down or restarting, ie set a preference to 0 seconds delay. Anyone know how I can do this?
Many thanks
Roger

---

### Post by olskar on 2009-09-24
> **rogerdean said:**
> Hi all
I'd like to remove the 60 seconds dialogue box when I'm shutting down or restarting, ie set a preference to 0 seconds delay. Anyone know how I can do this?
Many thanks
Roger

Think it used to be a setting in the preferences for the fast user applet thing if you rightckick it

---

### Post by wojox on 2009-09-24
If you right click the shutdown, (power button), top right, you can select preferences then uncheck "show confirm dialogs..." then when you hit shutdown it won't wait the 60 seconds.

---

### Post by NRDNick on 2009-09-24
I'm using Karmic and there appears to be no preferences option in the context menu when you right click the "Indicator applet session" on the top right of the screen. It seems the fast user switching app is a thing of the past.

---

### Post by forumache on 2009-09-24
> **NRDNick said:**
> I'm using Karmic and there appears to be no preferences option in the context menu when you right click the "Indicator applet session" on the top right of the screen. It seems the fast user switching app is a thing of the past.

So true.

---

### Post by utnubuuser on 2009-09-24
Try Alt+F2, then gconf-editor, then apps.

---

### Post by coldReactive on 2009-09-24
> **wojox said:**
> If you right click the shutdown, (power button), top right, you can select preferences then uncheck "show confirm dialogs..." then when you hit shutdown it won't wait the 60 seconds.

I didn't know that, thank you very much :3

---

### Post by rogerdean on 2009-09-24
not in karmic i don't think...

utnubuuser, i'll try to follow your way. where should i go after 'apps'?

cheers

...edit
aha, got it. it's apps -> indicator-session

---

