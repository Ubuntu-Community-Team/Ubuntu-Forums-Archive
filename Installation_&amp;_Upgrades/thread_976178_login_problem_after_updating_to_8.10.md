---
title: "login problem after updating to 8.10"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Kaspertje on 2008-11-09
After upgrading from 8.04 Hardy Heron to 8.10 Intreped I am unable to loging in. The login screens (as before in version 8.04) apears but my mouse nor my keyboard are available.

Could somebody please indicate me which packages that I 
could restore using apt-get in order to solve this problem?

My system showed a configuration problem before updating.
The configuration problem was due to updating to the last Hardy
Heron updates. My system blocked and I had to perform a hardware
reset. 

Thanks beforehand for help.

---

### Post by Carambouille on 2008-11-10
Hello,

I am facing exactly the same problem.
I had no issue during the upgrade from 8.04.
I launched dpkg-reconfigure xserver-xorg from a console but it did not help.

---

### Post by Carambouille on 2008-11-11
Hi again,

I found on a local Ubuntu forum ( [http://forum.ubuntu-fr.org/viewtopic.php?pid=2185072](http://forum.ubuntu-fr.org/viewtopic.php?pid=2185072) ) a turn around to move forward in the loging process and access to my desktop. It is not satisfactory...
I kill the X process and it restarts by itself with the proper settings for the keyboard and the mouse


In a terminal (CTR-ALT-F1) log in and

code:

pkill -9 X


Hope it can help to fix the bug.

---

