---
title: "Lock Screen Issues in Jaunty"
date: 2009-01-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-01-31
Hello,

My lock screen is wonky. Here are the behaviours:

[LIST]
[*]keyboard shortcut doesn't work
[*]when locked, if you try to enter password and it enter, it does NOTHING - just freezes at the "Checking" screen
[/LIST]

How do II fix this?

Thanks,
bobby
P.S. - will post to launchpad as well if no one responds.

---

### Post by SalsaDoom on 2009-02-27
wow, three weeks and no response?

I'm having the same issue. Very strange indeed -- perhaps it doesn't happen to everyone? Or perhaps no one else uses lock screen? :\

Cheers.
SD

---

### Post by avb on 2009-02-27
> **SalsaDoom said:**
> wow, three weeks and no response?

I'm having the same issue. Very strange indeed -- perhaps it doesn't happen to everyone? Or perhaps no one else uses lock screen? :\

Cheers.
SD

i dont have this issue on latest jaunty with gnome. Check /var/log/syslog after reboot, seems something pam related.

---

### Post by woosht on 2009-03-10
I have the same issue on my 9.04 workstation, gnome-screensaver and the lock screen command work the first time, that is the screensaver activates and though I can't use the mouse to stop it, a keypress brings up the password prompt. Entering the pw closes the prompt but gnome-screensaver is still running, I have to ssh in or switch to another tty to kill the process. After that, lock screen and gnome-screensaver no longer work.

---

### Post by syko21 on 2009-03-11
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/321311](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/321311)

It exists, please report on the issue

---

### Post by jmmL on 2009-04-18
I also have this problem. I have experienced it maybe 3 times in the past week.

I haven't yet found a way to reproduce the bug; I lock the screen maybe 5 times a day, and mostly it's fine. Other wise I have to switch to a VT and kill gnome-screensaver. Top shows that CPU usage of gnome-screensaver is ~99, i.e, one core of my dual-core processor.

The bug report claims the fix is released, but I'd say there has been another regression.

---

