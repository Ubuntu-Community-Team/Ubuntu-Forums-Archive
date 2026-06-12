---
title: "Lots of Bootup Messages"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by fluentbit on 2007-04-28
I've recently upgraded my Edgy server install to Feisty server. For the most part, things went smoothly. During bootup, I see the regular message about services starting up. Right after I'm displayed the login prompt additional services seem to be spewing messages to the console screen From what I can tell, the messages printed are related to my firewall rules and SMART bootup stuff, etc.

Is there a way to quiet these messages?

---

### Post by rcpettit on 2007-05-09
I have the same problem.  Everything worked normally with a bare base system but as soon as I installed Apache2, Mysql and such, it started displaying their startup messages after the login prompt is displayed and I have to hit enter to get the login prompt back.

---

### Post by mlind on 2007-05-09
Does your kernel entry in grub contains **quiet** option? It's usually defined in /boot/grub/menu.lst like this
```

# defoptions=nosplash quiet

```
(if you alter menu.lst's automagic options, make sure you invoke sudo update-grub)

---

### Post by rcpettit on 2007-05-13
Tried that but it didn't work. Still displaying the apache2, mysql, etc startups after the login prompt is displayed.

---

