---
title: "Notification Area and Multiple Keyboard Layouts"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HalfEmptyHero on 2010-03-06
I have 2 keyboard layouts, one for english and one for arabic. In karmic I didn't have to have the keyboard indicator applet on my panel, however, in lucid it seems that this was now put into the notification area. I feel it is a waste of panel space, as I can simply use keyboard shortcuts to change layouts. Is there any way for me to remove the keyboard indicator from the notification area?

---

### Post by go_beep_yourself on 2010-03-07
I'm not using Lucid, but look in System>Preferences>Startup Applications and see if it is listed in there to start after you login. If it is, you can uncheck or remove it.

How are you changing the keyboard layout with keyboard shortcuts? I am also using Arabic and English keyboard layouts, and with the indicator, it has been changing on it's own at random.

---

### Post by Funnnny on 2010-03-07
> **HalfEmptyHero said:**
> I have 2 keyboard layouts, one for english and one for arabic. In karmic I didn't have to have the keyboard indicator applet on my panel, however, in lucid it seems that this was now put into the notification area. I feel it is a waste of panel space, as I can simply use keyboard shortcuts to change layouts. Is there any way for me to remove the keyboard indicator from the notification area?

That is Ibus/SCIM                                                  ?

---

### Post by HalfEmptyHero on 2010-03-09
> **go_beep_yourself said:**
> 
How are you changing the keyboard layout with keyboard shortcuts? I am also using Arabic and English keyboard layouts, and with the indicator, it has been changing on it's own at random.

If you go into keyboard settings, you should see a tab or something with advanced options (or something similar to this, I'm not on gnome right now), and you will see a bunch of dropdown menus, one of which says hotkey to change layout. 

[QUOTE=Funnnny]That is Ibus/SCIM                                                  ?     [/QUOTE]
Well I know I'm not using SCIM, so I guess its Ibus.

---

### Post by matera.ttp on 2010-03-27
I have the same issue.
[https://bugs.launchpad.net/bugs/549654](https://bugs.launchpad.net/bugs/549654)
But they don't want fix this.
Does anyone know how to remove the keyboard applet from the notification area?

---

### Post by Funnnny on 2010-03-28
Right click on it, choose preference, Untick the checkbox "Show icon in system tray".
It'll still run, but there's no icon

---

### Post by chrisccoulson on 2010-03-28
> **matera.ttp said:**
> I have the same issue.
[https://bugs.launchpad.net/bugs/549654](https://bugs.launchpad.net/bugs/549654)
But they don't want fix this.
Does anyone know how to remove the keyboard applet from the notification area?

**Sigh**

Nobody (presumably you mean me?) said that we don't want to fix this. Your bug was specifically about resurrecting the missing keyboard indicator applet, which we're not going to bring back.

If you actually search, there is already a bug about introducing a preference to show/hide the new status icon which we do want to fix. But, your bug report didn't ask that

---

