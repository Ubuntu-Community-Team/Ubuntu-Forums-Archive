---
title: "[Kubuntu 21.10] Linux firmware update introduced lines across display"
date: 2021-12-16
forum: Installation &amp; Upgrades
---

### Post by jdeer2 on 2021-12-16
Ive been using kubuntu for a month now with no problems but this latest "linux firmware update" (i dont remember the update number, it was about 190MB in size and prompted me to update to it today december 16th) has created a couple lines across the bottom of my desktop. This is not present during bootup until it reaches the KDE plasma loading screen prior to entering the DE, and then persists during the session. The snapshot of it does not show the line but it does show that there is a gap between the taskbar and the bottom of the screen as is evident when you look at the highlighted folder which previously touched the bottom of the screen. This appears to be about 6-10px's wide. A three pixel line on the very bottom appears to change color as i scroll down a webpage. Graphics settings still show 1920x1080 at 60hz. The computer is a dell latitude 5490 laptop, mesa intel integrated UHD graphics 620. Is there a way to undo this update?

[IMG]https://i.postimg.cc/251DVrW9/Screenshot-20211216-135352.png[/IMG]

---

### Post by MAFoElffen on 2021-12-18
If it was indeed a Package Update that caused a problem, the correct thing to do is to file a bug report to Launchpad against that package, so that the problem with the update can be identified and corrected.

You can rollback a package by forcing the installation of an earlier version of that package, but that is not a permanent solution, and there are other things that would need to be done. Sometimes, that does not work out, and cause other problems, because other packages may be dependent on certain package versions. Things update eventually.

---

