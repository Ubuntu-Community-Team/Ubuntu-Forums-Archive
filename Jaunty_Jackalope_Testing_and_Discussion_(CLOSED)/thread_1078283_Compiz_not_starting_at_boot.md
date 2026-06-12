---
title: "Compiz not starting at boot"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-02-23
I'm sure this is probably a symptom of upgrading (opposed to a fresh install) but my compiz wont start unless I launch it manually.

I don't reboot/log-off that often so it's not critical, but it harms the desktop experience and it's going to get annoying pretty fast.

---

### Post by WatchingThePain on 2009-02-23
Hi,

Under 'system, preferences,  sessions' you can add compiz to the list. There's also an app' in the repositories called switch which is very convenient as it's a button on the panel that lets you switch compiz on and off as required.

---

### Post by chrisccoulson on 2009-02-23
> **WatchingThePain said:**
> Hi,

Under 'system, preferences,  sessions' you can add compiz to the list. There's also an app' in the repositories called switch which is very convenient as it's a button on the panel that lets you switch compiz on and off as required.

You shouldn't need to add Compiz to System -> Preferences -> Sessions. gnome-session already tries to start a window manager - this will just make it try to start 2 window managers.

What is the contents of the gconf key "/desktop/gnome/session/required_components/windowmanager"?

---

### Post by OliW on 2009-02-23
> **chrisccoulson said:**
> What is the contents of the gconf key "/desktop/gnome/session/required_components/windowmanager"?

compiz

---

