---
title: "new install freezes after login"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by jmyers on 2005-08-10
i recently installed ubuntu 5.04 on my laptop (an hp pavilion ze2000z), and when i log in, i get the startup sound (amidst much crackling) and the splash screen which reads "Ubuntu Linux for human beings." right there it freezes.  nothing responds except the power button, which is the only way i can do anything.  also, if i select "session" on the default login screen and choose one of the options, it locks up as soon as i click the radio button.  i've seen this problem on other forums but i couldn't find a solution that worked in any responses.  i have checked the error logs for xorg and gdm and couldn't find anything seriously wrong.  the laptop has an ati radeon xpress 200m with shared memory, an AMD Sempron 3000+, 512mb ram, integrated wireless and an 80GB hard drive, 40 of which currently holds windows xp home. if someone has fixed this problem, please let me know what you did.  thank you

---

### Post by jmyers on 2005-08-11
ok i did some more fiddling around with it today, and i found a forum that says that the ATI radeon xpress 200m is not supported in linux.  so i trieds the "vesa" driver in my xorg.conf instead of "ati" and "radeon", neither of which worked.  well, the vesa driver worked fine, so now the problem is fixed.

---

