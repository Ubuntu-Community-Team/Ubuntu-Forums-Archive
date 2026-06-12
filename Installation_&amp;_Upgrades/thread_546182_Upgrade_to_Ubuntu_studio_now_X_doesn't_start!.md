---
title: "Upgrade to Ubuntu studio now X doesn't start!"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by sluricanewallace on 2007-09-08
I did a clean install of Ubuntu studio 7.04 over my older 6.something version of ubuntu.  installation had no errors but when I did first boot it gave me this:

Fatal Server error:
Caught signal 11.  Server aborting

XIO:  Fatal IO error 104 (connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining.

I also have been unsuccessful in getting into the configuration utility as I am unsure of the command.

help!

---

### Post by Herman on 2007-09-08
Hello sluricanewallace,
Try this link and see if anything in there will help you, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")   sudo dpkg-reconfigure xserver-xorg (video, keyboard & mouse drivers, settings).

If you still need help, post back here again sometime with as many details as you can like what kind of monitor and graphics card you have and anything else you think might be worth mentioning.
Regards, Herman :)

---

