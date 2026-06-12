---
title: "onboard crashes xserver"
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marmuta on 2008-12-19
When I click any key in onboard X goes away and restarts. 
Could someone try to reproduce that? 
Does it happen with anything other than the radeon os driver I'm using?

I think it started with the latest xserver updates to 1.5.99.3. There is no hint in the logs of whats happening.

---

### Post by ShirishAg75 on 2008-12-19
marmuta, almost all the known chipsets are having issues, intel, ATI, Nvidia almost all seem to have problems (driver issues).

---

### Post by marmuta on 2008-12-19
Well, I was trying to figure out if it really was a graphics driver problem. Apparently it isn't, it segfaults in some keyboard code.

I've just filed bug [#309785]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/309785").

It could still use a confirmation to get it kicked-started. So no matter the graphics driver, whoever wants to do some testing, just run onboard in a terminal and see if it crashes X when clicking any button. Comments in the bug report are very welcome.

Thanks guys.

---

