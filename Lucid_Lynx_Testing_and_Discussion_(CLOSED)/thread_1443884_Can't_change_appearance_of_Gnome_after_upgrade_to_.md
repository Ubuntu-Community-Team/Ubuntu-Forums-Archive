---
title: "Can't change appearance of Gnome after upgrade to 10.04"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cheator on 2010-03-31
Just upgraded to 10.04 Beta last night. Everything seems fine but I can't run the "Appearance" menu under System > Preferences. When I run it from the command line I get this:

```
(gnome-appearance-properties:4233): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

```

Any ideas? I had some custom skins from gnome-looks installed, could this be the issue? If so, where are they so I can delete them?

---

### Post by Mark Phelps on 2010-03-31
10.04 is in beta testing and will be for a while.

You should be posting your beta-related questions to the correct forum: Development & Programming, Lucid Lynx Testing.

Will be asking the Mods to move this thread there.  Look there for any future responses.

---

### Post by Cheator on 2010-03-31
> **Mark Phelps said:**
> 10.04 is in beta testing and will be for a while.

You should be posting your beta-related questions to the correct forum: Development & Programming, Lucid Lynx Testing.

Will be asking the Mods to move this thread there.  Look there for any future responses.

You're right, I apologise for the misplacement.

---

### Post by mc4man on 2010-03-31
> 
Any ideas?
It's been fixed, just update.
(you may need to run the update manager twice - you want to get to this version
gnome-control-center (1:2.30.0-0ubuntu2) to [COLOR="Blue"]1:2.30.0-0ubuntu3[/COLOR]

---

