---
title: "gusty harddrive activity and swap"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by wilsho on 2007-11-14
I recently upgraded to gutsy from feisty on a Dell inspiron 530.  In general, I'm quite happy with the upgrade but have one annoying problem.

When I first boot the system everything proceeds normally and I get my normal desktop.  If I do nothing (just stare at the screen) there is no disk activity.  However, shortly (within 5 seconds) after starting any application, I start to get disk activity that is so intense that everything slows to a crawl.  This goes on for  several minutes.  If I continue, it will recur periodically, but never stop completely.

I have 2 GBytes of memory and using "system monitor" I notice that I ALWAYS end up with 34.5 MBytes of SWAP being used.

However, if I then reboot the system and return to my Desktop, for the rest of the day I never again get intense disk activity and my system never uses SWAP again... it stays at "0" usage.

Any thoughts/help would be appreciated.

wilsho

---

### Post by Rmantingh on 2007-11-27
Could it be that Tracker is kicking in after you first access any application
(or in other words: make a change to any of the files on disk)?
Tracker is the application that indexes all your files for easy searching.
I don't use this myself and always remove it first thing after an install.

To check what is running you could open a terminal and issue the "top" command.
This shows the topmost processes using the CPU (to stop - press Q).

---

### Post by wilsho on 2007-11-28
Thanks, but in the process of troubleshooting I completely removed Tracker with no effect.

wilsho

---

