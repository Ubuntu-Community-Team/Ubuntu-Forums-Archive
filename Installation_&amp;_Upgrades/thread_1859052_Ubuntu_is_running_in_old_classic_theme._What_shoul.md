---
title: "Ubuntu is running in old classic theme. What should i do to run unity?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by vikash_chandola on 2011-10-13
Windows 7 ultimate runs with all of it's effects but Ubuntu is not running with unity it runs in fall back mode(with classic looks). What should i do to run unity.
oops sorry; i think i post it in wrong place.Can anybody(mentor/admin) please move this thread to general discussion.:(

---

### Post by dave2001 on 2011-10-13
At the login screen, you can choose your desktop environment. Select your username, right click, and choose the "Unity" option. (that's if your using 11.10).  If your using 11.04, there will be a dropdown menu titled "session" at the bottom of the login screen where you'll choose the "Unity" option. 

If Unity still does not load, then there may be an issue with your graphics card/driver. To see if there is a proprietary driver available for your graphics card, go to System Settings> Additional Drivers.

If neither of these things works, you might want to post your system specs so we have a better idea what the issue might be.

---

### Post by vikash_chandola on 2011-10-13
> **dave2001 said:**
> At the login screen, you can choose your desktop environment. Select your username, right click, and choose the "Unity" option. (that's if your using 11.10).  If your using 11.04, there will be a dropdown menu titled "session" at the bottom of the login screen where you'll choose the "Unity" option. 

If Unity still does not load, then there may be an issue with your graphics card/driver. To see if there is a proprietary driver available for your graphics card, go to System Settings> Additional Drivers.

If neither of these things works, you might want to post your system specs so we have a better idea what the issue might be.
none of method works
system specs 
Intel Pentium 4, 2.7Ghz
1 GB DDR2 RAM
for more info on graphics see attachments

---

### Post by dave2001 on 2011-10-14
hmm you've got an 82xx integrated intel video chip. I have an old dell with one of those, and it's glitchy with anything above 10.04. If I recall it's because of an issue with the intel driver not working properly with the 82xx chips, and so one of the generic low performance drivers (vesa or fbdev) get's loaded instead.
I could not find a fix for this issue. I just bought a new $25 nvidia video card and use that instead of the integrated intel.

---

