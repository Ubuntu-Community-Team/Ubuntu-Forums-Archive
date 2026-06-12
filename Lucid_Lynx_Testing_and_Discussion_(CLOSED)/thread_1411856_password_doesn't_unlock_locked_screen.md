---
title: "password doesn't unlock locked screen"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by robertbub on 2010-02-20
Typing in my password does not break the lock after doing "lock screen" or getting the lock screen via the screensaver.  It just sits there.

This was after I did a "aptitude safe-upgrade" this morning; it was working fine before.

If I CTL-ALT-F2 to a getty term and kill gnome-screensaver, the lock is broken.

Mostly annoying presently.

---

### Post by robertbub on 2010-02-20
I think the problem may be the Gnome Keyring Daemon because when I tried rebooting, it said that it was stuck.

I don't understand why the keyring daemon is necessary for unlocking the screen, however.

---

### Post by LKjell on 2010-02-20
Too many bug report on the same thing and it does not look like they are fix or very old so I made a new one. 

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/525030](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/525030)

You can either disable locks or login to another tty and manually kill the gnome-screensaver processes.

---

