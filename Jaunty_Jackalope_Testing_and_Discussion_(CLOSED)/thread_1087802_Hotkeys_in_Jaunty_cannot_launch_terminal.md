---
title: "Hotkeys in Jaunty: cannot launch terminal?"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hatdragon on 2009-03-05
I'm not sure if I discovered a bug in Jaunty, but I can no longer set a keyboard shortcut to launch a terminal. I always use "Alt+`", but I tried that and several other random key combinations, and none of them work--when used, either the application I'm in captures the key press and tries to do something with it or nothing happens at all. My other keyboard shortcuts seem to all work properly, but I haven't tried any other custom configurations for them. Any ideas?

---

### Post by Tim Sharitt on 2009-03-07
I was having the same problem, I had Alt-F3 assigned to launch the terminal in keyboard Shortcuts, but it did not work (neither did Alt-F2 fo Run Application). I had to enable Gnome Compatibility in CompizConfig Settings Manager (gconf should work as well) then assign the proper shortcut keys.

There are only a few key under Gnome Compatibility as most are under General > Key Bindings in CompizConfig Settings Manage or apps > compiz > general > allscreens > options in gconf.

The only thing I have yet to figure out is how to get my multimedia keys working, so I am open too any suggestions ;)

Edit: My play/pause, stop, forward, back buttons started working (magic maybe...or it could have been that overdue update ;) but the volume control buttons still do not work.

---

### Post by hatdragon on 2009-03-07
Thanks! I wouldn't have thought of looking in Compiz settings, although that makes sense now. The issue has been fixed.

---

