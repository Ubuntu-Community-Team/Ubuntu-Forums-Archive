---
title: "Fresh install kubuntu alpha6 64bit - no plasma desktop..."
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xlnt01 on 2009-03-13
I just did a fresh install of kubuntu alpha6 64bit and now the desktop wont start. Plasma crashes...
When I run plasma manually I get:
plasma(12266): Communication problem with "plasma", it probably crashed.

Hopefully there will be an update really soon to fix this problem.

---

### Post by kayosiii on 2009-03-13
sounds like plasma is only half dead... try killing it before starting it again... 

killall -9 plasma

---

### Post by perlluver on 2009-03-13
This is a known bug, and they are working on a fix for it.  I hope it hits the repos soon.  I would like to mess about with KDE.

---

### Post by xlnt01 on 2009-03-13
I found the report:
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/338205](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/338205)
Hopefully the fix will hit the repo's real soon...

---

