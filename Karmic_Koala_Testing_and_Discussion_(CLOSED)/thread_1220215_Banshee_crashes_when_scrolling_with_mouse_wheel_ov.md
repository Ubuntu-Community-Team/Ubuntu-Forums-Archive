---
title: "Banshee crashes when scrolling with mouse wheel over notification icon"
date: 2009-07-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Craigy90 on 2009-07-22
Hey all,

I am running banshee from the repositories (version 1.4.3) and whenever I scroll down with the mouse wheel over the notification icon for banshee, while a song is playing, banshee crashes.

I don't exactly know how I should report this bug (just ubuntu-bug banshee?) and provide all the necessary info. Banshee doesn't seem to have great integration with apport :confused:.

Thanks.

---

### Post by Marat89 on 2009-07-22
[Banshee Bugzilla Site]("http://bugzilla.gnome.org/browse.cgi?product=banshee")

---

### Post by MacUntu on 2009-07-22
I can reproduce this bug (maybe it's not directly connected to the tray thing but just caused by changing songs rapidly?) but how do I get a backtrace of mono apps?

**Edit:**

To get a stack trace I attached to the running process and set gdb to handle the signals SIGPWR and SIGXCPU:

```
(gdb) handle SIGPWR nostop noprint
(gdb) handle SIGXCPU nostop noprint
```

that gave me (kinda) useful output.

---

### Post by MacUntu on 2009-07-22
Opened a bug report upstream: [http://bugzilla.gnome.org/show_bug.cgi?id=589441](http://bugzilla.gnome.org/show_bug.cgi?id=589441)

Please confirm, if you can. :)

---

### Post by Craigy90 on 2009-07-22
Sorry, I don't have confirming powers. I see that you got a backtrace, thanks for all your effort!

---

