---
title: "Screen doesn't unblank after opening lid"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-12-15
Whenever I close my lid in Lucid regardless of whether doing so blanks my screen, suspends, or hibernates my machine, I can't return to my desktop after opening my lid.

I have an Dell Inspiron 640m with Intel 945gm.

How do I bring my lid events back to sanity?

---

### Post by lisati on 2009-12-15
Does your machine do anything when you press a key or move the mouse?

---

### Post by Starks on 2009-12-15
Even with only opening the lid, the desktop is "restored", but the screen remains blanked. Restarting X through keypresses doesn't help either and only returns me to a login prompt with a still-blanked screen.

Rebooting is the only thing that works.

---

### Post by Starks on 2009-12-15
BTW, this solution works for me: [http://ubuntuforums.org/showpost.php?p=8448660&postcount=25](http://ubuntuforums.org/showpost.php?p=8448660&postcount=25)

It's very crude and I don't like using it.

---

### Post by Starks on 2009-12-22
This is a system-crippling bug and I don't understand why people don't care about it. Perhaps I need to bug more relevant people on IRC.

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/496842](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/496842)

---

### Post by jpeddicord on 2009-12-22
I can confirm the issue here, however check your report for some needed information. I haven't really been closing my laptop lid except to put it in standby, but it does break when I do. :P

---

