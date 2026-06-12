---
title: "No Splash Screen on Start-up"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by bwsmith25 on 2010-05-03
I recently installed Ubuntu 10.04 on my laptop (clean install, not upgrade), and when I turn my computer on, I get a black screen instead of the purple "Ubuntu" screen before my system logs on. When I log off, I get the purple "Ubuntu" screen, but not when I log on. Is there a fix for this?

---

### Post by davidedwardpurcell on 2010-05-04
I have exactly the same problem under Kubuntu 10.04. Still not found a fix.

---

### Post by Alan F on 2010-05-04
Upgrade from Ubuntu 9.10 has produced similar all black screen during boot, otherwise no problems.

---

### Post by bwsmith25 on 2010-05-04
> **davidedwardpurcell said:**
> I have exactly the same problem under Kubuntu 10.04. Still not found a fix.

I installed Kubuntu 10.04 to try it out, and I had the same problem as I do with Ubuntu 10.04 - there are no other issues with booting, but I would like to see the nice purple boot screen instead of an all black screen.

---

### Post by morbido007 on 2010-05-04
same problem with 9.10->10.04 upgrade

---

### Post by Alan F on 2010-05-04
Anyone?

---

### Post by salemboot on 2010-05-07
1. sudo dpkg-reconfigure plymouth

normally dpkg-reconfigure will work for failures.  

2. sudo apt-get remove plymouth && sudo apt-get install plymouth

if all else fails:guitar:

---

