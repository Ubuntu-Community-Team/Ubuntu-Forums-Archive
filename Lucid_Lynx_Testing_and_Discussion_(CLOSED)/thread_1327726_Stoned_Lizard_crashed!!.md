---
title: "Stoned Lizard crashed!!"
date: 2009-11-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-11-15
I have been on here all day.

Boinc is running full bore.

Just trying to help folks that have the attitude that they were paying no attention and now someone needs to bail them out.

Fired up synaptic to look at what was available in the "science" section.

Was doing so.

Screen goes blank and then starts running some kind of fs problem stuff for several minutes for sdb7 (/home) and then start over for sda8 (/).  Occasionally it would throw up a CLI login but never long enough to use because it was off again.

Alt + SysRq + b = no effect.  Pulled plug.

Went recovery mode and checked for broken packages.  Nothing.  So return to normal boot takes me to CLI log in.

Log in, run startx, back up like nothing happened.

WTF?

---

### Post by ronacc on 2009-11-15
nothing in any of the logs ?

---

### Post by ranch hand on 2009-11-15
I really have to admit that I have no idea where to start looking.  I am back on 9.04 now but was, just now, rumageing around in the /var/log files and I see nothing there having to do with a running system, which is when this occured.

Well, after looking again, this may be it (I was looking for a directory not a file) from /var/lib/messages - forget that it is just the startup stuff, all looks clean.

I am back to - what logs?

---

### Post by VMC on 2009-11-15
Since you said it went blank, look at the .xsession-errors and .xsession-errors.old for any tell tale signs.

---

### Post by ranch hand on 2009-11-15
Now see, I knew I didn't know what I was doing.

That is kind of interesting.  The boinc thing doesn't surprise me, the volume stuff in probably connected in that boinc keeps the cpu s at 100%.
> 
(boincmgr:2267): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkwidget.c:9567: widget class `GtkPizza' has no property named `row-ending-details'

** (gnome-settings-daemon:2180): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:2268): WARNING **: Connection failed, reconnecting...

(boincmgr:2267): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkwidget.c:9567: widget class `GtkPizza' has no property named `row-ending-details'

(boincmgr:2267): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkwidget.c:9567: widget class `GtkPizza' has no property named `row-ending-details'

(boincmgr:2267): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkwidget.c:9567: widget class `GtkPizza' has no property named `row-ending-details'

(boincmgr:2267): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkwidget.c:9567: widget class `GtkPizza' has no property named `row-ending-details'

(boincmgr:2267): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkwidget.c:9567: widget class `GtkPizza' has no property named `row-ending-details'

** (gnome-settings-daemon:2180): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:2268): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2180): WARNING **: Connection failed, reconnecting...
Goes on for pages like this.

I may have to tweek boinc down a bit if this keeps up.

Thanks for pointing me the right direction.

---

