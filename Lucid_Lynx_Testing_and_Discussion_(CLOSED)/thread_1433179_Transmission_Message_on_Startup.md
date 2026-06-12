---
title: "Transmission Message on Startup"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ghindo on 2010-03-18
I'm running Ubuntu Lucid with the most recent updates.  I have Transmission (1.91-0ubuntu2) configured to start upon login, but every time it starts it gives me a warning.  (See attached picture.)  I looked around in the Transmission preferences and couldn't find a way to disable it.  It's a bit cumbersome to deal with this warning so frequently!

Has anyone else experienced this?  I'll post a bug report if this isn't a known issue.

(I apologize if this has already been posted, I checked the forums and didn't find anything.)

---

### Post by _h_ on 2010-03-18
Does it keep appearing on each startup even when you click I Accept?

---

### Post by ghindo on 2010-03-18
> **_h_ said:**
> Does it keep appearing on each startup even when you click I Accept?Yes, it does.

---

### Post by _h_ on 2010-03-18
> **ghindo said:**
> Yes, it does.

Interesting, can't find anything on the transmission forums about it. Maybe post a support topic on their forums?

---

### Post by Longinus00 on 2010-03-18
Make sure the permissions for /home/USER/.config/transmission/settings.json are correct. If it keeps happening then delete the file and let transmission make a new one. You might also want to look in the message log to see if there are any messages related to writing the settings file.

---

### Post by ghindo on 2010-03-25
Latest round of updates seems to have fixed everything.

---

