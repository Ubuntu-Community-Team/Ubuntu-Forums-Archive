---
title: "How to upgrade to 10.10 (beta) from 9.04"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by linuxnovice. on 2010-09-12
Ok so i have 2 pcs 
one is running lucid lynx and when I use the command update-manager -d I get the option to upgrade to 10.10
but on my second pc I'm running 9.04 (jaunty jacklope) and when i run the command update-manager -d I only get the option to upgrade to 9.10.

so how can I upgrade from 9.04 to 10.10 without having to install the following versions.

---

### Post by drs305 on 2010-09-12
Ubuntu isn't designed to allow upgrades by skipping releases such as you want to do. You can update from release to release (9.04 > 9.10 > 10.04 > 10.10) or from LTS to LTS (8.04 > 10.04), but not from 9.04 > 10.10. 

You would have to upgrade to 9.10 then upgrade to 10.4, even if you did it the same day. Of course, a clean install is always an option for any release and many users prefer than method even when an online upgrade is available.  ;-)

Added: The most important thing is to get 9.04 completely updated and then upgrade to 9.10 if that is how you plan on doing it, as 9.04 reaches its End of Life next month.

---

### Post by Rubi1200 on 2010-09-13
+1 to everything said by drs305.

I just want to add one friendly word of caution:

10.10 is currently in beta, meaning that it is not intended for stable production environments.

From the Ubuntu website:

> **This is a beta release. Do not install it on production machines. The final stable version will be released on October 10, 2010.**

---

