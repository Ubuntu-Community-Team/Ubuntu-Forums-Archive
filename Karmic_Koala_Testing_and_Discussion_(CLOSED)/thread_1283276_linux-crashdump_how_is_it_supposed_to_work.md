---
title: "linux-crashdump: how is it supposed to work?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pedrogfrancisco on 2009-10-05
Using Kubuntu, don't know if in Ubuntu the results are the same.

I'm at a loss to understand the functioning of [linux-crashdump]("https://wiki.edubuntu.org/KernelTeam/CrashdumpRecipe").

Here is what I expected:
* kernel panics
* "backup" kernel boots
* "backup" kernel saves a dump of the memory, maybe printing some messages to the screen
* computer restarts or asks to be restarted.

Here is what I see:
* kernel panics
* "backup" kernel boots
* "backup" kernel access disk a lot
* seems to get stuck in Terminal (VT), cursor not blinking;
* Alt+SysRq+E results in X starting afterwards, to exit a few minutes late and start again.


So, what may be happening? When is it supposed to save the memory dump?

---

