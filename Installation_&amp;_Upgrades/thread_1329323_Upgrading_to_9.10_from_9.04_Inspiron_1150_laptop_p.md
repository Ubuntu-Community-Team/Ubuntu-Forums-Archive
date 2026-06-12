---
title: "Upgrading to 9.10 from 9.04 Inspiron 1150 laptop problems..."
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by sh00t on 2009-11-17
Have hit some hurdles installing 9.10 on my inspiron 1150 laptop.
I used the update manager to update and install 9.10 and when I got home from work I had to yes/no a couple of things before it finished off and restarted. Which [COLOR="Red"]after restart it shows the black&white ubuntu logo and goes to a terminal, no desktop interface[/COLOR] and of course ifconfig and iwconfig are screwed up too...

update:
the startx will bring up the desktop but then dump out... says something about glx and no nvidia drivers but i did install them .. i'll post back later, on diff comp now, was easily able to get wifi up on command line, was scared about that at first, had issues with previous releases...

---

### Post by grege on 2009-11-17
Your video problems might be solved from here .....

[http://ubuntuforums.org/showthread.php?t=1309667](http://ubuntuforums.org/showthread.php?t=1309667)

the 1150 and 1100 are essentially the same.

---

### Post by sh00t on 2009-11-17
ok, tried installing the nvidia x86 190.42.pkg1.run but it errors out. I get this message (EE) Failed to initialize GLX extension (Compatible NVDIDIA X driver not found) Waiting for Xserver to shut down Dropping Master ddxSigGiveUp: Closing log

---

