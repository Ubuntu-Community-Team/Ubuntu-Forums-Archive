---
title: "Linux kernel image 2.6.15 problem"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by qrees on 2006-06-03
I've noticed that udev doesn't work with old kernel so I installed new one. Now udev seems to work, but KDE and GNOME stopped working (After login i see only terminal window but in graphic mode). Not even in failsafe. This is strange because:

1. graphics is working
2. Everything is fine with old kernel, apart from that udev does work

So now I can choose: music+TV or KDE...

Please help...

---

### Post by qrees on 2006-06-03
bump

---

### Post by qrees on 2006-06-03
Maybe this will help:

[IMG]http://wiki.qrees.info/startkde.png[/IMG]

This is what I get after startkde. Sometimes at the end there is also:

```
ICE default IO error....
```

---

### Post by qrees on 2006-06-03
When I ron startkde as root everything is working, so this is probably problem with user profile, but I don't know what do I have to do... Anyone?

-----
When I run kdestart as normal user xrdb takes a LOT of cpu time and seems to hang... After killing it kde loads.

---

### Post by qrees on 2006-06-03
problem seems to be solved. Again... no one did answer it and I had to look for the solution by my self :evil: 

1. I copied .kde dir from /root/ folder and chowned all files in that dir.
2. chmod 777 /dev/null (but i'm not sure if that is correct setting, anyone? )

---

### Post by blimpyboy on 2006-06-04
chmod 666 /dev/null is the one

---

### Post by qrees on 2006-06-04
Well, but i have now new problem. Whenever i reboot system i have to chmod /dev/null . It's always set to 700 at start. I have 2.6.16.19 kernel from kernel.org. (but the same problem is with kernel from ubuntu).

---

