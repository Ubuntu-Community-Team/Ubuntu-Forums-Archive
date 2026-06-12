---
title: "Upgrade to 11.04 from 10.10-Unity Issues"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by leitrimlover on 2011-07-03
When I upgraded to 11.04, Ubuntu classic works fine. However, when I log into the Unity Ubuntu, all that shows up is the background, and Desktop Items. No task bar at the top (containing the time, shutdown etc) or side panel bar, with the shortcut items.

Now, while I was using 10.10, I installed 11.04 as a clean install on a different partition of my laptop. Therefore I have the system requirements. However, the upgraded 11.04 causes Unity issues.

Hopefully, someone will know how to rectify this issue. I cant seem to see what is happening. 

Thanks

Dave!

---

### Post by dino99 on 2011-07-03
if the laptop is recent, it can run unity (3d) by using a decent graphic chipset/card, otherwise install , with synaptic, either:
- unity-2d
- gnome-shell
-gnome-session-fallback

into a terminal, you can restore the settings:
depend on your login choice
- unity --reset
- unity --replace
- gnome-panel --replace
- gnome-shell --replace

---

