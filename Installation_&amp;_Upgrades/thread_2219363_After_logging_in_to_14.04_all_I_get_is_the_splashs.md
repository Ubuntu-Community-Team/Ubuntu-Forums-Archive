---
title: "After logging in to 14.04 all I get is the splashscreen"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2014-04-23
I just did an automatic upgrade from 13.10 to 14.04.  After logging in normally and as a guest I just get the purple/pink slash screen with Ubuntu 14.04 in lower left of screen, and that all.  I have tried numerous suggestions on the forum but so far nothing has helped. Finally out of desperation I went to terminal mode (Ctrl+Alt+F1) and typed in firefox.  I got the following errors:
GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size=0' failed
Error: no display specified

I am not sure where to go from here.  Any suggestions?

PS: I am having to enter all this from a Windows computer which is driving me crazy!

---

### Post by mörgæs on 2014-04-24
How does 14.04 work in a live boot?

---

### Post by Baasha on 2014-04-24
> **mörgæs said:**
> How does 14.04 work in a live boot?

Unfortunately, I can not live boot because I don't have any DVD discs, this was an online automatic upgrade.  When I go to terminal mode with a ctrl+alt+F1 I sometimes get a list of services that are running and lightdm is among them, so at least I know that is working.  The problem seems to be with the display as noted above. While I was playing around I tried opening Gedit from the terminal and again I got a message saying "cannot open display".  I have tried loading both the Nvidia and Nouveau video drivers but neither one has any effect on this problem.

---

### Post by p.callan on 2014-04-24
I had the same problem today, and it turned out that the drivers for my ATI radeon GPU were not working properly. Uninstalling them completely fixed it all. Check this out, and especially the last link in post #5:

[http://ubuntuforums.org/showthread.php?t=2219503](http://ubuntuforums.org/showthread.php?t=2219503)

---

