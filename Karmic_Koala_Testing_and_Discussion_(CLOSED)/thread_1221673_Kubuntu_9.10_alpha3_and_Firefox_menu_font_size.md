---
title: "Kubuntu 9.10 alpha3 and Firefox menu font size"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by The Cog on 2009-07-24
I thought I'd try out kubuntu/kde and see how it looks these days. I have to say on the whole, it's looking very good, and I might start using KDE rather than Gnome. I much prefer dolphin to nautilus. 

However, I have an issue with the firefox font size under KDE. Particularly the menu fonts. I found a GTK+ settings configuration in the system settings, but it doesn't appear to have any affect on the firefox menus (I did try restarting firefox). There must be a way to adjust this - what am I missing?

---

### Post by dualscreenman on 2009-07-24
The default GTK+ theme that Kubuntu uses, QtCurve, grabs its font settings from what you have configured as your KDE fonts. I plan to put a little text blob in the config module for its next bugfix release.

---

### Post by Asraniel on 2009-07-24
perhaps a dpi issue? try to change the dpi settings (will also affect kde fonts)

---

### Post by The Cog on 2009-07-24
> **dualscreenman said:**
> The default GTK+ theme that Kubuntu uses, QtCurve, grabs its font settings from what you have configured as your KDE fonts. I plan to put a little text blob in the config module for its next bugfix release.

I don't fully follow what you mean here, but I have made some progress. I have found that if set for QtCurve, then the font settings are ignored completely and all gnome applications have oversized menu fonts. If I change the widgets setting to raleigh instead, then the menus pick up the configured fonts perfectly but all the gnome applications (firefox, geany, wicd) have apallingly ugly widgets. I'm not sure which option is worse. Do you know if there's any way to get the QtCurve setting to use the configured fonts?

I'd post screenshots, but I havent' figured out how to take them yet.

---

### Post by sam81 on 2009-08-28
> **The Cog said:**
> I don't fully follow what you mean here, but I have made some progress. I have found that if set for QtCurve, then the font settings are ignored completely and all gnome applications have oversized menu fonts. If I change the widgets setting to raleigh instead, then the menus pick up the configured fonts perfectly but all the gnome applications (firefox, geany, wicd) have apallingly ugly widgets. I'm not sure which option is worse. Do you know if there's any way to get the QtCurve setting to use the configured fonts?

I'd post screenshots, but I havent' figured out how to take them yet.

have exactly the same problem, still haven't figured out how to fix it :confused:

---

### Post by sam81 on 2009-08-31
The problem was solved for me just by modifying the kde font settings. See here for details: [https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-qtcurve/+bug/420610](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-qtcurve/+bug/420610)

---

