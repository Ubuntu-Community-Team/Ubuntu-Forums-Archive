---
title: "update manager entering password twice"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-10-06
Anyone else get the problem where update manager requires entering their password twice?

The first prompt is "Authentication is required to install software packages".

The second prompt, after you enter your password for the first one, is "Authentication is required to upgrade software packages".

Anyone else get this issue?

---

### Post by zoomy942 on 2009-10-06
i was yes.  i generally use the terminal to update, but thought i would try this for kicks.  and sure enough, it wants a password twice.

---

### Post by Peter09 on 2009-10-06
Yep - same here

---

### Post by Grimhound on 2009-10-06
Same. And sometimes the second time fails and spawns without the text box and results in me having to forcibly kill it... which in turn sometimes causes the update to lock up and forces me to backpedal and relog.

---

### Post by Longinus00 on 2009-10-06
**edit**

Found the bug on launchpad, looks like it's fixed and will get pushed out sometime in the future.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/437094](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/437094)

---

