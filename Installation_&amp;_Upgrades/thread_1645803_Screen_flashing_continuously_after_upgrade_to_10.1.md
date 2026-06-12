---
title: "Screen flashing continuously after upgrade to 10.10 from 10.04"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by kimiboy on 2010-12-15
I was using netbook remix 10.04. Yesterday I upgraded the OS to 10.10 using alternate iso. After the restart I'm facing two errors.

[LIST=1]
[*]modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory

I got a solution for the above error after searching the forums. Now my 2nd error is


[*]When the system tries to login, my screen starts flashing with just the ubuntu netbook desktop wallpaper on the screen. No other options will be available. It will be flashing continuosly. If I press the power button then one window comes up with options like Shut down, Restart, Hibernate etc. And the screen won't stop flashing either. I've uploaded a 1 min video. Please go through it as it will give you a clear idea of the error which I'm facing now. [[COLOR="Blue"]Click here for the link[/COLOR]]("http://www.twitvid.com/8UUW4")
[/LIST]

---

### Post by sikander3786 on 2010-12-15
First of all, try to logout and once on the login screen, click your username. Sessions menu will appear in the bottom of your screen, select ubuntu-desktop and login. Does that encounter the same problem?

---

### Post by kimiboy on 2010-12-15
Thanks sikander3786. It worked :D

Solved both the issues.

I edited initramfs.conf for solving the first one and changed the default session to ubuntu-desktop in System -> Administration -> Login Window for solving the second one.

---

### Post by sikander3786 on 2010-12-16
You might need to install the graphics proprietary drivers from System > Administration > Additional Drivers and then, you might be able to use the ubuntu-netbook DE as well.

Good Luck!

---

