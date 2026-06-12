---
title: "Help me please!"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by soni08 on 2008-08-09
I have been running ubuntu 7.10 without any problems until now.I clicked on the update icon, everything was fine, until the downloading stopped on its own without completing the up dates. I decided to restart my computer and now when I try to start the computer I get past my login and the screen is blank. If I try to run it in safe mode the only error message that appears highlighted is vm.mmap_min_addr and I still cannot run ubuntu. I would really appreciate some help asap!

---

### Post by TenPlus1 on 2008-08-09
Maybe the HD was busy when you reset and you corrupted something...  Some updates will pause the system to check a few things so you gotta be patient, but to get you up and running quickly, so a fresh install to make sure it's all installed OK...

---

### Post by hyper_ch on 2008-08-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by SkonesMickLoud on 2008-08-09
Are you able to get to any rescue terminals?  To do this, press Ctrl+Alt+F1 - F6 until a terminal comes up.

If/when it does type in:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

When it's done, press Ctrl+Alt+F7 to get back to your GUI.

How long did your previous attempt stall for?

---

### Post by soni08 on 2008-08-09
Thanks for your help TenPlus 1, I guess your right about waiting it out. I have started a reinstall as I figured it was my only option.

---

