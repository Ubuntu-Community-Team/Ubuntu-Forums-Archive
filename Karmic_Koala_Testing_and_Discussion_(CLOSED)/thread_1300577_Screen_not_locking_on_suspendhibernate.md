---
title: "Screen not locking on suspend/hibernate"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lieter on 2009-10-25
I've got a Sony FW51JF laptop, which works fine. 

I got it a few days ago and installed karmic on it(fully updated). Now I've got a problem. The screensaver doesn't kick in(locks) when i suspend or hibernate.

I've activated lock the screen in the screensaver properties
Via Gconf-editor I've activated suspend and hibernate in apps/gnome-power-manager/lock
And /etc/default/acpi-support has LOCK_SCREEN=true set.

I've got no idea what to enable to get the screensaver to kick in and ask me for a password when returning from suspen/hibernate.

any idea's?

---

### Post by papangul on 2009-10-25
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/407315](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/407315)

---

### Post by Lieter on 2009-10-25
I've looked at that big report(and the one that it's a duplicate of) and they appear to have fixed the problem. Using the gpm chooser it works fine, and using the indicator applet is locks fine. However, i suspend/reboot/whatever the laptop using the Session Management plugin for Gnome-Do. And looking at the icon displayed when activating suspend via gnome-do has led me to believe that it calls the same suspend function. But apparently it doesn't. I'll try to see why it doesn't(ergo, looking at the code).

But to do that i need to know what does the suspend option in the indicator applet call?(the function or command).

---

### Post by Lieter on 2009-10-25
It appears that this is already a bug:
Bug #410079 and Bug #377672, marking thread as solved.

---

