---
title: "resolution problem in 9.10"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by LinFreeman on 2010-01-13
I just upgraded from Ubuntu 9.04 to 9.10.  That fixed many of the small annoyances of 9.04, but produced a major problem.  I am running a Dell Inspiron B130 laptop (with a Intel GMA 950 graphics card).  I have been using it with a Samsung LCD external monitor (Synchmaster 2494).  Under 8.04, 8.10 and 9.04, the external monitor worked fine. I was able to set its resolution to 1920x1080 while leaving the Dell's monitor at 1024x768.  But under 9.10, if I uncheck "Mirror screens", choose the (already available) Resolution option 1920x1080 and click on "Apply", both screens turn black and freeze. I have to manually turn the Dell off and restart it.  Then, of course, it has reverted to 1024x768.  I don't want to run my Samsung at 1024x768.  Does anybody have any suggestions?

I've discovered that I can change the resolution with the command:

xrandr -s 1920x1080

But that doesn't hold through reboot.  How can I make it do that?

---

