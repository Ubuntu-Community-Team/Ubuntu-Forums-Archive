---
title: "gconf overloading CPU?"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-08-29
Is anyone else having trouble with gconf overloading the CPU.
Earlier today I experienced a problem with Compiz, so I restarted Compiz, and now whenever Compiz is running, the process gconfd-2 is taking up 20% of the CPU

---

### Post by jfernyhough on 2009-08-29
I'm sure this has been covered before.

After a
$ compiz --replace

you need (at the moment, maybe with a sudo)
$ killall metacity

as the compiz script does not correctly kill a running metacity instance.

---

### Post by andresmh on 2009-08-31
This worked but... what are the implications of killing metacity?

---

