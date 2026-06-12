---
title: "Lucid on Acer Aspire One: Metacity crash"
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by k64 on 2010-01-23
If I run "wget" in a terminal and open Firefox at the same time, on my Acer Aspire One, Metacity crashes. Has this bug been reported in Launchpad already? If not, as soon as Metacity crashes, nothing else will run. Of course, this is with Compiz enabled. However, it seems as though Compiz tries to run without Metacity, and pushes Metacity out of memory when these two programs (WGet and Firefox) are running.

This bug is fairly new, and better get fixed by the time Lucid is final.

---

### Post by k64 on 2010-01-23
Still non reply? It's been an hour!

---

### Post by ranch hand on 2010-01-23
Bumping threads before 24 hours is frowned on.

Reply to what?

There is no question, just a statement.  Seems straight forward.  Don't run wget and FF at the same time.

---

### Post by ronacc on 2010-01-23
did you file a bug ? if so link to it . if not how do you expect it to get fixed ? have you done anything to find out exactly what is causing the crash ?

---

### Post by Ibidem on 2010-01-25
You NEVER have Metacity running at the same time as Compiz...that's how window managers work. 
Check which one you have running in the task manager or "top".
But that sounds like it may be Firefox or wget that cause the problem, with a major crash resulting from some problem.
Questions: are you starting wget after firefox, firefox after wget, or both at about the same time?
If you run another window manager (Openbox, IceWM, etc.) instead, how does it work?
Are you accessing different servers or the same one?

---

