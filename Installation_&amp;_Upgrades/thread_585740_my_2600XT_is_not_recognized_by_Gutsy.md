---
title: "my 2600XT is not recognized by Gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by unzzi on 2007-10-21
Feisty worked somewhat okay with newest ATI 8.41.7 fglrx drivers (after meddling with xorg.conf a bit). Compiz ran with XGL but had some problems with titlebars disappearing (got that fixed later on) and some programs wouldn't run with XGL loaded (open office was one of them, a major problem for me).

Now that I upgraded and tried to changed some things through "Screen and graphics" menu every time I start up Gutsy I get a pop-up saying my graphics hardware wasn't recognized and I'm running on low-graphics mode because of that. I also tried restricted drivers, changing options through "Screen and graphics" and editing xorg.conf in several different ways. It's like editing xorg.conf doesn't have any effect at all and the same pop-up at start keeps appearing no matter what I try to change. Tried with fresh Feisty install and upgrade to Gutsy from that too. Same problem. Anyone know where's the problem and how to fix it?

edit: Might have found the problem... It won't complain while using generic VESA drivers so it seems my problem is with drivers. X.org wiki says the following about ATI fglrx drivers:
> The set of drivers still is bound to XFree86 4.0.0 and X.Org 6.7.0, but might get updated to be compatible with the latest X.Org release. Further updates and inclusion of GLSL are expected for one of the very next releases.
Gutsy has X.org 7.3, right? Seems like a huge mess to get it working. I'm relatively new to all this so, am I **** out of luck until ATI releases a driver that supports X.org 7.3?

---

