---
title: "[SOLVED] Anjuta is unstable after upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by ksadil on 2007-10-19
Anjuta is terrible after the upgrade to gutsy. In particular, glade3 plugin crashes anjuta every time. I also expected glade3 to create stubs in callbacks.c, but I cannot get it to work.

Ideas?

---

### Post by ksadil on 2007-10-19
Otherwise gutsy upgrade went very well.

---

### Post by josephus on 2007-10-19
I've had trouble with anjuta crashing after the upgrade as well.  Ended up just uninstalling and reinstalling the old version using the feisty packages.

---

### Post by kh_naba on 2007-10-22
That is packaging problem. See the following bug report:
[https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/125343](https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/125343)

---

### Post by kh_naba on 2007-10-24
While waiting for gusty official integration, you can get the new builds from Rob's repository:

Add deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy universe

---

### Post by ksadil on 2007-11-25
A bit late I know, but thankyou very much. Works fine now.

---

### Post by roberto.ur on 2008-02-05
grrrrr

it is "main" not "universe"
deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy main

or
deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy main universe

i don't know if there is actually something in universe

hours hours.... grr

---

