---
title: "&quot;Show Icons In Menus&quot;  - Checkbox Broken"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Static- on 2009-10-19
System > Preferences > Appearance > Show icons in menus


this toggle box doesnt work, no matter what i do icons will not go away.


ive tried looking through gconf-editor with no avail :(

---

### Post by Static- on 2009-10-19
anybody?

---

### Post by mcduck on 2009-10-19
The gconf key is desktop/gnome/interface/menus_have_icons.

---

### Post by Static- on 2009-10-19
didnt do anything

---

### Post by psyke83 on 2009-10-19
Because of the recent [design decision]("https://bugs.launchpad.net/bugs/407621") to disable icons on buttons and in menus, icons that are "whitelisted" will always get displayed, even if the gconf key "desktop/gnome/interface/menus_have_icons" is disabled.

While I strongly disagree to this recent decision, surely if we are to proceed with this change, the problem of certain icons being explicitly displayed is a bug. This has effectively re-defined the setting from a boolean that will either enable or disable icons, to a boolean that will either enable icons, or partially enable icons.

P.S. The System -> Preferences -> Appearance setting controls the gconf key, so they're identical.

---

### Post by Static- on 2009-10-19
thats terrible, looks like ill be sticking with 9.04 and older if this stays.

---

### Post by mcduck on 2009-10-20
> **Static- said:**
> thats terrible, looks like ill be sticking with 9.04 and older if this stays.
Unless that setting will change back in the future (which I doubt), that leaves you with a year of time left with using Ubuntu. (and Gnome, since the change was done by Gnome, not Ubuntu).

Well, a year should be enough of time to find out something else to use. And of course if you are happy with running unsecure system with no packages available because of couple of icons you can of course use some outdated release even longer. :)

---

### Post by cyberkilla on 2009-10-21
I was trying to hide _all_ of the icons on menus, but I noticed that most of them stuck around. Not particularly useful any more, if the preference doesn't keep it's word:)

Does Ubuntu Karmic beta bundle a stable version of GNOME right now, or does it somehow become stable around the time Karmic is released officially?

---

### Post by 6205 on 2009-10-21
IMHO i think it's OK to have some icons in menus and now when i don't have icons on buttons i have realized that i like it more :)

---

### Post by cyberkilla on 2009-10-21
> **6205 said:**
> IMHO i think it's OK to have some icons in menus and now when i don't have icons on buttons i have realized that i like it more :)

Perhaps, but when you specifically select "no icons in menus" from the preferences, it should show _no_ icons, or reword the preference, surely? I might be having a different issue to the one discussed here.

---

### Post by Static- on 2009-10-21
well some people.. like myself remove the icons from all menus. 

for aesthetics
for load times


i dislike icons, and i was quite happy with the option to turn em off. 


so with this problem and the IPV6 issues im having, eff 9.10, i just re-built this box with Arch Linux:P

---

### Post by MacUntu on 2009-10-21
> **cyberkilla said:**
> Does Ubuntu Karmic beta bundle a stable version of GNOME right now

Yes, Gnome 2.28.0 it is.

---

