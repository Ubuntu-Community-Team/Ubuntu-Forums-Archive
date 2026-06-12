---
title: "Not Resuming from Suspend (12.04)"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by mikeymo1741 on 2012-05-29
I've noticed after my recent upgrade to 12.04, that every once in a while, when I close the lid on my laptop, it will not resume properly on opening. 

I'm using a Dell Inspiron 1300, and Ubuntu Studio 12.04.   The power settings have it suspending on lid close.  Most of the time, opening the lid causes it to resume to the login box.  

Every once in a while, though, it will power up and I will get the desktop background and a mouse cursor (which works) and nothing else.  No matter how long it sits, it will not give me the login box.  Even if I re-suspend it (either by closing the lid or hitting the suspend button) same thing.  I need to restart it, then it works fine.  

I was wondering if anyone else is seeing this?

---

### Post by krustenBrot on 2012-05-30
+1

same problem... tried killing the processes or restarting unity via terminal, does help from time to time but most of the time it just gets stuck again :/



):P

---

### Post by 2F4U on 2012-05-30
Some information on your hardware as well as what graphics driver you are using could help diagnosing the problem.
There is a log file dedicated to suspend, /var/log/pm-suspend.log, and you should look into it after a failed suspend.

---

