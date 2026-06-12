---
title: "&quot;Other&quot; in Menu"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gunksta on 2010-04-20
For the past week or so, I have had a menu entry called "Other". When I look at the menu entries in "Other", I see a listing, in alphabetical order, of practically every application on the system. It starts at Abiword and continues to Yelp. It includes the X apps, mc, the tcl shell, the erlang shell etc. And, it uses the OLD school gnome-style icons.

So, when I use Alt-F2 to start Gedit, I don't see the modern "Human" icon. I see the old-school Gnome 1.x Gedit icon, which looks like ####. Finally, I have gbrainy installed. It's cute. But, it is not in my games menu. I can only find gbrainy in the "Other" menu.

I tried using main-menu to revert the menu, but it didn't help. I can fix the icon issue by simply hiding this menu, just like we do with the Debian Menu. But, if I ever install an application that only appears in the "Other" menu I'll never see it. Is there any way to clean this up?

---

### Post by ranch hand on 2010-04-20
I had to look for the "other" menu.  If you have a lot of stuff on there you may want to re install gnome-menus.

---

### Post by gunksta on 2010-04-20
No dice. Do change.

I should mention that I do have gnome-shell installed (just to play with it). I think I may have noticed the change after installing gnome-shell. Out of curiousity, I tried removing gnome-shell (and it's immediate deps) and tried reinstalling gnome-menus and python-gmenu. Again, no change. I still have a "Other" menu with lots of choices.

---

### Post by ranch hand on 2010-04-20
Weird.  I would just move them where you want them then, after filing a bug on one of the menu packages.

---

### Post by jaco223 on 2010-04-20
If you right click on Applications you can edit the menus, and remove the Other listings.
I don't know if you can actually remove Other though.

---

### Post by ranch hand on 2010-04-20
You can have it so that other does not appear but you would want to add the ones you want to other menus first.

---

### Post by gunksta on 2010-04-20
I've got the "Other" Menu hidden right now. The really weird part is that it is a full re-listing of all the apps. Take Abiword for example. It is sitting in Applications --> Office, just like it should be. It is ALSO in Applications --> Other, which is not where it should be.

I guess I should create a dummy user to see for sure if this is related somehow to my config or if it is system-wide.

---

