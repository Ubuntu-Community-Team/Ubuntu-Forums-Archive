---
title: "Ubuntu 10.04 freezes when booting"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by tigars53 on 2010-05-26
Hi, I just upgraded from 9.10 to 10.04 and everything was working fine at first.  Then today when I tried to boot ubuntu 10.04 the computer freezes on the first loading screen of ubuntu, the one juste before the login page.
I tried loading in failsafe mode, but I'm not able to have any graphic interface, only command line.

Can someone help me with this?

---

### Post by oldfred on 2010-05-27
From recovery are you able to run updates. sometimes that helps.

From the command line can you run
startx

That will start the graphical interface if it will work. Or you may have a better idea of the issue.

---

### Post by tigars53 on 2010-05-27
I got it, thank you!

I tried typing "startx" in the terminal in failsafe mode and it basically gave me this:
parse error line 25 in file /usr/lib/xorg.conf.d/0-wacom.conf : "option" not a valid keyword in section

I just modified that trying to set my wacom graphic pen right before ubuntu decided to freeze at boot. I had no idea this could have had an incidence on the loading of the graphic interface...
So I just modified the file back to how it was before and now ubuntu boots fine.

---

