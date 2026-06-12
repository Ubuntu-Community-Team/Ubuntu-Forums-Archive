---
title: "Logging out on its own"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by TechnoSapien on 2007-04-11
I am using the latest version of edgy. I always keep the updated current. There were 3 or 4 updates that comae out last night. I installed them and rebooted when prompted. Now I can log into a session but after a few minutes it will suddenly revert to the login screen. This also happens when I "lock screen" .  Everything else seems to be working ok.  Thanks in advance for your help.

---

### Post by petersjm on 2007-04-11
Same here, if anyone can offer any help... Came back from Easter break and installed ten or 15 updates, now it seems to log itself out without any input from me...

---

### Post by TechnoSapien on 2007-04-19
This is still happening. Has anyone else run into this?

---

### Post by shasan on 2007-04-19
This may not be applicable to what is occurring for you, but if I remember that xgl has a 'feature' that will log you out if you hit SHIFT+Backspace. This happened to me quite a bit before I realized what was going on.

---

### Post by TechnoSapien on 2007-04-19
I dont think that is quite it. Thanks though. I can even configure a kb shortcut to lock the screen, when I usit it logs me out also.

---

### Post by TechnoSapien on 2007-04-20
I think this is the problem.

[http://ubuntuforums.org/showthread.php?t=278693&highlight=disable+Gnome-screensaver](http://ubuntuforums.org/showthread.php?t=278693&highlight=disable+Gnome-screensaver)

---

### Post by petersjm on 2007-04-23
> **TechnoSapien said:**
> I think this is the problem.

[http://ubuntuforums.org/showthread.php?t=278693&highlight=disable+Gnome-screensaver](http://ubuntuforums.org/showthread.php?t=278693&highlight=disable+Gnome-screensaver)

Yep, screensavers were the problem. More specifically, OpenGL screensavers. I'm not sure which update caused this to happen on my box, but after I upgraded to Feisty, the problem has gone.

---

