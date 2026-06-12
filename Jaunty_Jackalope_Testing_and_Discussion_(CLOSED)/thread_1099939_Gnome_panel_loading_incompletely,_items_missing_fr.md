---
title: "Gnome panel loading incompletely, items missing from system tray?"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bastanteroma on 2009-03-18
The gnome panel shows up when I login only as a blank bar. If I open a terminal and type "gnome-panel --replace" the newly started panel seems to work fine, except that sometimes NM applet doesn't appear in the systray, nor does any volume control applet. (That's where it's supposed to be now, right? The standalone applet doesn't show up at all in the panel if I try to add it.)

Changing themes has also crashed the panel, forcing me to restart it in the same way.

---

### Post by Bastanteroma on 2009-03-27
Does anyone at least know how to purge all the config maybe, or any other ways to fix it?

I completely removed gnome-panel, but when I reinstalled it, it immediately resumed the same config, meaning that something was left behind.

EDIT: Made a new panel and deleted the old one. Seems to have worked.

---

### Post by Wonslung on 2009-03-29
i have the same  problem...i deleted the panel and made a new one but i'm still noticing weirdness...
i can't get the volume applet to work at all, it never shows up.

when i try to go to system>preferences>sound it never starts....i DO have sound though but i can't change any settings.....

it's very frustrating

---

### Post by alastair on 2009-03-29
Yes, something similar here. Downloaded and booted the actual beta "live" cd and my first reaction (apart from disappointment at still needing the acpi=off option to boot at all) was - where are the panel menus? Initially I thought it was some sort of silly Gnome re-design .. but quickly discovered the panel was "broken" somehow. 

So, downloaded a daily live and tried again - better. I have most menus - but the panel doesn't have the volume control (but terminal alsamixer worked) plus it seems to die eventually. After 5-10 mins or desktop use, both top and bottom panels die and beccome faceless dead grey bars ... until a "--replace" brings it back - for a while.

H/W :
Shuttle SG33 - Core2 Quad
Intel G33 / ICH9
Intel video driver

Seems to happen with Compiz on or off.

Alastair

---

