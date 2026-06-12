---
title: "upgrade problem today (4.11-3 to 4.11-5): kde-runtime"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by udippel on 2014-02-11
Received my usual notice of an upgrade today (Feb. 11), and did it. Got a lot of files, KDE update. At the end, it displayed an error, and after reboot, I can still log in, but that is user name and password, but then no session comes up. X is up, of course, but the start-up splash screen does not come up. I can see its background, but nothing else happens. Same for my account and guest account.

On a command line, apt-get update and apt-get upgrade result in "... 2 not upgraded." and these 2 are kde-runtime and plasma-scriptengine-javascript. When I apt-get install kde-runtime, it says that it depends on kde-runtime-data 4.11.5 or larger, but 4.11.3 is to be installed. "you have held broken packages".

What now?

---

### Post by henrikm85 on 2014-02-11
Same here :-(

---

### Post by henrikm85 on 2014-02-11
I was able to install it after apt-get update now so someone must have fixed it. No idea if I can log in again though since I am not at the office anymore.

---

### Post by udippel on 2014-02-11
Yes. But I had to sudo apt-get install kde-workspace-bin kde-runtime plasma-scriptengine-javascript before the choice of KDE popped up at the logon prompt.

---

