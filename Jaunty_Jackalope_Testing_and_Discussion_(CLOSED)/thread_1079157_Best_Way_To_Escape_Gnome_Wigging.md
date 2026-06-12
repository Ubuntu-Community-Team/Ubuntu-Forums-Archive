---
title: "Best Way To Escape Gnome Wigging"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-24
If I manage to get gnome to wig out and the desktop stops responding rather than reboot Ive been doing:

TTY1
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

And then relogging in via GDM

Is there a better way?

EDIT: As you might have guessed Im having problems with gnome and apps that stop responding. Im currently doing a memory test on my test system.

---

### Post by Hairy_Palms on 2009-02-24
if ctrl-alt-backspace is still not working then u could always do alt-sysrq-K

---

### Post by taavikko on 2009-02-24
Is it GNOME that's going haywire, or some app?
Personally I would to try kill the app before restarting whole gdm.

BTW, I use ```
sudo invoke-rc.d gdm restart
```
If all else fails...

---

### Post by taavikko on 2009-02-24
> **Hairy_Palms said:**
> if ctrl-alt-backspace is still not working 

It's not, since it's been disabled by default, courtesy of upstream.
It can be enabled via dontzap...

And by killing "sysrq+k" all processes and/or gdm restart,
all work might get lost, so use sync before that...

---

