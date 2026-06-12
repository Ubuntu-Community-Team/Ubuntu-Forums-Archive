---
title: "command &quot;tput reset&quot; closes terminal now"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-09-25
Folks, instead of closing the terminal's window it's supposed to just clear the terminal screen.
Anyone knows whether it's some kind of new weird feature or a bug?

---

### Post by dinxter on 2009-09-25
still works ok here, not much help i know :)

---

### Post by froggyswamp on 2009-09-25
Weird, I use default settings except for fg and bg colors.. and the terminal closes, using x64 Karmic with all updates.

---

### Post by froggyswamp on 2009-09-25
Did more testing, it crashes when there's many lines to clean up, see attached short video I recorded.

---

### Post by dinxter on 2009-09-25
yep, that breaks it for me too, sounds like bug material

---

### Post by dinxter on 2009-09-25
think it may bring down the tty as well

[EDIT] Forget that, i was early morning confused, tty seems ok

---

### Post by dinxter on 2009-09-25
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/436102](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/436102)

think that may be it

---

### Post by MacUntu on 2009-09-25
Yes, that's it. Just backtraced it and got the info from the bug report.

Above bug is now a duplicate of [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/435367](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/435367)

---

