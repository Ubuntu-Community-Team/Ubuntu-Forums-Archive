---
title: "Notification area vs indicator applet?"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Madspyman on 2010-03-13
In Lucid why are all the notification icons split between the indicator applet and the notification area? Are both necessary? Couldn't we just stick with one unified area for everything?

---

### Post by castrojo on 2010-03-13
Eventually: [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

---

### Post by 23meg on 2010-03-13
> **whiprush said:**
> Eventually: [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

And, [http://gould.cx/ted/blog/Having_a_tidy_systray](http://gould.cx/ted/blog/Having_a_tidy_systray).

---

### Post by Keyper7 on 2010-03-13
It's like the old saying:

"Rome wasn't built in one day, Caesar had to patch a lot of upstream projects."

Or something like that. I don't remember the exact saying.

---

### Post by Madspyman on 2010-03-13
Thanks for the information, can't wait till it's finished. However, I've run into a related problem, currently in Lucid gnome-shell has no support for the indicator applet, but the notification area works fine, until everything is unified with gnome-shell support, would there be anyway to get all my notifications (Rhythmbox, volume applet ect..) back into the notifications area like in Karmic, so I can use gnome-shell correctly again?

---

### Post by Half-Left on 2010-03-13
> **Keyper7 said:**
> It's like the old saying:

"Rome wasn't built in one day, Caesar had to patch a lot of upstream projects."

Or something like that. I don't remember the exact saying.

Well ok, but KDE4 did massive amounts of work like this in about three, six month releases. KDE 4.0 looks totally different from 4.4 and that was only 24 months.

---

### Post by Keyper7 on 2010-03-13
> **Half-Left said:**
> Thanks for the information, can't wait till it's finished. However, I've run into a related problem, currently in Lucid gnome-shell has no support for the indicator applet, but the notification area works fine, until everything is unified with gnome-shell support, would there be anyway to get all my notifications (Rhythmbox, volume applet ect..) back into the notifications area like in Karmic, so I can use gnome-shell correctly again?

Yes. By design, if an instance of indicator-applications is not found running, it gracefully falls back to the traditional notification area icon.

If you see this not happening for some application, it is a bug that should be reported.

I'm not sure about indicator-sound, though. whiprush?

> **Half-Left said:**
> Well ok, but KDE4 did massive amounts of work like this in about three, six month releases. KDE 4.0 looks totally different from 4.4 and that was only 24 months.

It's important to remember that the indicators are not the only thing the developers are working on.

Furthermore, your KDE example refers to developers working to modify *their own project, that they intimately know*.

Spreading application indicators involves working with *several different upstream projects*, sometimes *without being familiar with their code*.

---

### Post by Madspyman on 2010-03-13
> **Keyper7 said:**
> Yes. By design, if an instance of indicator-applications is not found running, it gracefully falls back to the traditional notification area icon.

If you see this not happening for some application, it is a bug that should be reported.

I'm not sure about indicator-sound, though. whiprush?

Thanks, yeah I had to add indicator for sound (gnome-volume-control-applet) back to the startup applications and log out and back in, all is working now though. I don't know why I didn't just try to delete the indicator applet in the first place.

---

