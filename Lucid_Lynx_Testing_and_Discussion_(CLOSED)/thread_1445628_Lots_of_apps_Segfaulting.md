---
title: "Lots of apps Segfaulting"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wedderburn on 2010-04-02
hey, upgraded to lucid awhile ago, fairly clean upgrade no real issues 

however a number of apps all segfault when run they include:
Rhythmbox
Software-center
empathy
gwibber

and from the games
lightsoff
swell-foop

no expert but i imagine theres some shared files between all these apps thats causing the screw up.
tried a new user and got the same results 

now this computers been running ubuntu since 5.10 Breezy Badger so there may be files lurking from then that are causing the issue.

**solved**
removed libicu and all traces of it, reinstalled ubuntu-desktop and all is good again :)

---

### Post by Cracauer on 2010-04-02
Last time I had that I `strace -f`ed and found a broken random GNOME plugin. Simply nuking the offending *.so file fixed the problem.

---

### Post by wedderburn on 2010-04-02
> **Cracauer said:**
> Last time I had that I `strace -f`ed and found a broken random GNOME plugin. Simply nuking the offending *.so file fixed the problem.

that helped get rhythmbox working again, a libicu removed that and rhythmbox works again, unfortunately i removed all the software that depended on the library :P but thanks this gives me something to go on.

---

