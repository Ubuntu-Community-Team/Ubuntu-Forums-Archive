---
title: "everything broken"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tretle on 2009-03-26
Rebooted today to find a really long pause between the gdm and gnome session. Also the theme is broken, a weird sound theme has applied.. pidgin is broken, gstreamer is broken, bonobo, indicator applet etc. Is anyone else experiencing these issues, its not my hardware as i have already tested the drive and memory.

---

### Post by Mr. Picklesworth on 2009-03-26
Sounds like gnome-settings-daemon is crashing. Maybe versions are out of sync.
Have you tried restarting?

---

### Post by tretle on 2009-03-26
several times with no success :( though it does give a crash report for the settings daemon whenever i try and open the appearance preferences.

---

### Post by Reiger on 2009-03-26
Try a purge & reinstall from terminal?
```

sudo aptitude purge -y ubuntu-desktop && sudo aptitude install -y ubuntu-desktop
```
Might just fix it.

Upon log on through gdm, drop to terminal with Ctrl,Alt + F2 and log in. Check you have working internet (e.g. via browsing to google with w3m: w3m [www.google.com](www.google.com)). If so, you can do the purge & reinstall thing.

---

### Post by tretle on 2009-03-26
that didnt work

---

### Post by Reiger on 2009-03-26
In that case it is **probably** something in your user account mucking it up. You could try to see if you can create a secondary user account that is member of the same groups your original (borked) account is. Then see if when you log on as the other user you get a proper desktop back?

If that does the trick, time for a step-by-step migration from borked_account -> working_account (moving documents, music and such).

When all is fine you can delete the borked account (remove any files under /home/$BORKED_USER_NAME/) and optionally re-name yourself again.

---

