---
title: "Upstart 0.5 not even in Intrepid?"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dentharg on 2008-09-04
Hi!

[http://upstart.ubuntu.com](http://upstart.ubuntu.com) mentions version 0.5 being released. Yet Ubuntu Packages mention 0.3 for Intrepid.

Is it safe to uprade yourself?

---

### Post by UbuWu on 2008-09-20
You could do that but it won't make much difference and you risk breaking your system. Ubuntu still uses the old bootscripts, started by upstart. For Jaunty, the version after Intrepid it is planned to convert them all to upstart jobs and start taking advantage of its features.

---

### Post by UbuWu on 2008-09-20
If you really want to experiment with upstart, follow the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=727224](http://ubuntuforums.org/showthread.php?t=727224)

And no it is not really safe, still very experimental.

---

