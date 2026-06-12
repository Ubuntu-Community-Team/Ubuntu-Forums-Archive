---
title: "Karmic reverse apport?"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-10-18
Whenever a new ubuntu distribution gets released I usually try to port a few friends to ubuntu.

However while doing so I often find that some of these friends have rare computers that are simply not supported well by ubuntu and linux.

Apport collects hardware information whenever a bug occures to improve bug reports.

Is the reverse process also possible? 

Scan hardware -> Find related bugs.


This would cause less failures and would reduce the amount of people thinking "Im having this bug but I think someone else will have reported it already, so why bother?".

So I think this will actually increase the change of a bug report happening when a false positive happens. Helping new users, and developers.

---

### Post by 23meg on 2009-10-18
Apport does not collect hardware information itself, but references information collected by Checkbox, if any, from the Ubuntu hardware database. What you suggest will be possible in the future when we have public interfaces for the hardware information collected by Checkbox.

---

