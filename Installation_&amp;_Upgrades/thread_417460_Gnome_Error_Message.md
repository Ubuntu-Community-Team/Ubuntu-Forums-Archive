---
title: "Gnome Error Message"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Pudwud on 2007-04-21
Since the upgrade I get this message on my main desktop:

“Cannot start the preferences application for your window manager
Window manager “unknown” has not registered a configuration tool”

Any suggestions?

Thanks.

---

### Post by jpeddicord on 2007-04-22
Are you using Beryl or Compiz (or even Desktop Effects)? That might be part of the problem, although I have not heard of any reports of it. Try running the following in a terminal and then restarting GNOME.```
metacity --replace
```

---

### Post by hangman_jdf on 2007-04-24
I had this problem too.  It happened after open office crashed, which may have crashed my printing job.  I restarted a couple times and that didn't help.  I type "metacity" into the terminal and everything started working again.  I am a noob, but I figured that I just needed metacity started again.  Some how the stalled out print job interfered with it?

---

