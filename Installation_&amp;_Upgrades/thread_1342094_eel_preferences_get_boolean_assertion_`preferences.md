---
title: "eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by fmpdmb on 2009-11-30
I recently upgraded to karmic and I believe this error starting showing up then.  From the terminal, if I run the command 'nautilus' I see the following.

[INDENT](nautilus:3674): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed[/INDENT]

nautilus seems to start up fine.  I'm just wondering if this should be a concern.

---

### Post by Kaedenn on 2009-12-16
Same here. One day, gnome-settings-daemon (I believe) failed to load, and I've yet to get it to load. Restarting, relogging or even ctrl+alt+bksp have no effect.

$ gnome-open .
(nautilus:4863): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

Help?

---

### Post by patman0623 on 2009-12-17
[https://bugzilla.gnome.org/show_bug.cgi?id=598918](https://bugzilla.gnome.org/show_bug.cgi?id=598918)

---

