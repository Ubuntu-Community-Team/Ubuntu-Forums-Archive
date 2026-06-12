---
title: "gdm won't start (reboots machine) after 11.04 upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by macho on 2011-04-30
I upgraded to 11.04 yesterday, and now gdm refuses to start. It actually reboots the machine, so it goes into an infinite loop of reboots if left alone. This happens even if I choose the previous kernel I had been using in grub. Safe mode allows me to boot to a terminal, and a USB flash drive boot still works.

Is there a way for me to dig into the logs to find out what is causing this? Anyone else experienced the same thing?

I'm running on a Sempron 140, not doing anything special that I can think of.

Thanks!

---

### Post by macho on 2011-04-30
Oh yeah, just to be clear, if I boot to a console then do

```
$ sudo gdm restart
```

It also reboots the computer, right about the point where I see a mouse cursor.

---

### Post by macho on 2011-05-01
OK! I've mostly figured it out. I moved all of my home folder config files ~/.* away and it starts fine. Which is good. Except I don't get to keep my previous configuration, which sucks, unless I want to track down whichever file caused the problem by trial and error.

---

