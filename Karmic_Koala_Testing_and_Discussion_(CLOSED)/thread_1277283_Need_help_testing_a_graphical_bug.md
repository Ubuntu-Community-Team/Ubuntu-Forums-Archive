---
title: "Need help testing a graphical bug"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stoffe on 2009-09-28
Hello friends, I would appreciate it if some people could help testing/verifying a bug I have. I see it on an ATI card, while someone else does not see it on an Intel card. Would be very nice if a few more people could test with or without ATI to see if it's a driver specific issue or something else.

The bug is here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/437863](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/437863)

The test case is easy:

* Install crack-attack (or other GLUT based application)
* Start the application
* Choose to start the game from the first screen that pops up
* See if the window decorations are invisible or not for the new window that opens

On my computer (ATI), and on my previous (which was Intel, and may be fixed), the decorations are invisible but possible to interact with.

Please report findings to bug report.

Thanks for your help!

---

### Post by moviemaniac on 2009-09-28
Window-decorations work for me. But then again I (have to) use the fglrx-driver (R600-based 2600XT)

---

