---
title: "update gdm and lose Xwindows"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2007-01-05
So far 3 times, I have used system - admin - update manger and have lost Xwindows when trying to reboot, it wont come up!
Me being a lowly linux newbie I have to wipe the partition and reinstall ubuntu.

Next I am going to try and ghost the partition from windows so I can restore it.

What do you think is causing this, It will boot normally, but at the end all I get is a gray screen.

What can you run to configure xorg.conf? from command prompt

---

### Post by gborzi on 2007-01-05
To reconfigure the Xserver, use the following command: > sudo dpkg-reconfigure xserver-xorg
hope this helps.

---

