---
title: "Shutdown and Restart gone from Ctrl-Alt-Del"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-01-16
Is it just my machine or someone else is having Shutdown, Restart missing from Ctrl-Alt-Del (power button) panel? Also, if I choose Shutdown and Restart from I get to login window. OK, I get to tty and do that myself, but...
In Network manager I can not edit connection anymore.
The only change I was testing these days was running without dpms... I've reverted all changes I made (removed PowerManager from StatUp and xset -dmps) but that did not help.

---

### Post by sliketymo on 2010-01-16
Still working here.

---

### Post by autark on 2010-01-16
I'm getting something similar after updating just a few minutes ago. For me, the "Shut Down" and "Restart" options are not gone but disabled. Like the OP, I cannot shut down or restart normally; I have to issue a shutdown command from a text console. But I can edit network connections just like before.

---

### Post by zika on 2010-01-16
NM is not important for me, I use ifupdown... I just tested it to get  ageneral picture what is causing this "trouble"... Now, that I'm not the only one, I'm cool.

---

### Post by VMC on 2010-01-16
> **zika said:**
> Is it just my machine or someone else is having Shutdown, Restart missing from Ctrl-Alt-Del (power button) panel? Also, if I choose Shutdown and Restart from I get to login window. OK, I get to tty and do that myself, but...
In Network manager I can not edit connection anymore.
The only change I was testing these days was running without dpms... I've reverted all changes I made (removed PowerManager from StatUp and xset -dmps) but that did not help.
I experience the shutdown/restart yesterday. I had to power cycle. On next boot it never did it again. I think some update fixed it.

The  Ctrl-Alt-Del or power button work as planned.

---

### Post by zika on 2010-01-16
> **VMC said:**
> I experience the shutdown/restart yesterday. I had to power cycle. On next boot it never did it again. I think some update fixed it.
The  Ctrl-Alt-Del or power button work as planned.My machine was powered off/on several times lately but the behavior of power button did not change. It'll come to senses eventually...

---

### Post by MacUntu on 2010-01-16
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/508379](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/508379)

---

### Post by zika on 2010-01-16
Everything is back, now! Thank You all.

---

