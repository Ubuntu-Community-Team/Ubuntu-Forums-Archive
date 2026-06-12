---
title: "not nice to use system ... some dialogs take ages to open"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-04-18
For a few days now I have a problem with dialogs/windows taking ages to open - and I have no idea what could be the problem.

E.g. in Firefox "Save Page as" (or "Save as" in any other program),
"New Mail" in Evolution, and many more.

Any ideas?

---

### Post by Mr. Picklesworth on 2009-04-18
I have had that pop up before, specifically with browsing through files even using terminal stuff like ls. Fixed with a restart and I never saw it again. Some kind of awful file system related bug. In retrospect, I should have saved the kernel logs...

---

### Post by excogitation on 2009-04-18
I thought I had already rebooted a few times...

After this restart it was way better but after some time it's back to slow.

Helped figure out the cause though.
I think this is related to my crashing tracker...
No idea what happens there, but when I kill it everything works again.

edit:
I was wondering why my CPU was suddenly so hot (70+°C) all the time ;-) now it's about 20°C colder.

---

### Post by Carl Hamlin on 2009-04-18
May or may not be related, but whenever I install a new release, one of the first things I do is smoke trackerd. That little ******* has caused a lot of trouble for me in the past.

---

