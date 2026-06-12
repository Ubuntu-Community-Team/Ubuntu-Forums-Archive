---
title: "Ubuntu and my monitor."
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by xira on 2005-03-19
Hi huys, I've tried installing Ubuntu, but it didn't work with my LCD. (Dell 1704FP which it detects) - I tried manually editing the X conf, but everything was set right (res, hsync etc) but whenever I would boot into X/Gnome the monitor would turn off

I'm using a Radeon 9800 Pro 256mb which it also detects. Any help would be appreciated!

---

### Post by Buffalo Soldier on 2005-03-19
Have you tried?```
sudo dpkg-reconfigure xserver-xfree86
```

---

### Post by xira on 2005-03-21
Yes, I did that. The problem remains.  :(

---

### Post by IdoMcFly on 2005-03-21
[QUOTE=xira]Yes, I did that. The problem remains.  :([/QUOTE]
 Does your graphic card have 2 outputs?

---

### Post by xira on 2005-03-21
Yes, DVI and VGA. I'm using DVI.

---

### Post by nis_ on 2005-03-21
Xira:

It's easier to troubleshoot the Xserver using 'startx' or 'X -probeonly'.  The log
found in /var/log/XFree86.0.log is also critical to understanding the source
of X11 startup problems.

Regards,

nis

---

### Post by IdoMcFly on 2005-03-22
look into the ATI driver documentation, maybe there is an option to force the output on DVI, maybe it is on analog output.

---

