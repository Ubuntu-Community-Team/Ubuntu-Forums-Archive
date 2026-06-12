---
title: "Video Probs After Feisty Fawn Upgrade"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Bill Bickley on 2007-04-24
Just upgraded to Feisty Fawn.  Now my applications (e.g., Firefox, Terminal, etc.) open in a window in the upper left portion of the screen which cannot be moved in the traditional fashion.  Have I set something incorrectly, is this a known issue with Feisty Fawn, or what?

The Show Desktop button doesn't work, either.  I get this message:  "Your window manager does not support the show desktop button, or you are not running a window manager."

Bill

---

### Post by dannyboy79 on 2007-04-24
[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg85784.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg85784.html)

---

### Post by Bill Bickley on 2007-04-25
"metacity &" solves the problem, but the solution does not stick.  Next time I boot up, same problem.  I don't find the ".gnomerc" file mentioned.

Apparently, these problems are a consequence of having fiddled with the enhanced desktop features without the necessary hardware.

Now what?

Bill

---

### Post by dannyboy79 on 2007-04-25
this is only a hack of a fix but you can add "metacity" to your startup programs list under system, preferences, startup programs. (NOTE: there shouldn't be an quotes around metacity)
Also, i could be wrong on the exact menu location for where to put this, but there is a place that you can add applications using a little gui that will be started upon bootup. Maybe it's under system, admin, startup programs. Let me know where it is when you find it. Also, now that you know the problem, you can start a new thread to find out how to get metacity to start automatically but correctly. good luck

---

