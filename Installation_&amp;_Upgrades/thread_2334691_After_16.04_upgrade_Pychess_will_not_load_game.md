---
title: "After 16.04 upgrade Pychess will not load game"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by lou6 on 2016-08-21
The title says it all - Pychess will no longer load a previously played game. It did this just fine on 14.04LTS.

I have uninstalled and reinstalled (more than once). Running in terminal shows many Gtk errors. If anyone has an idea on what I can do, please share.

This is the 3rd or 4th major problem I've had since installing 16.04.

I'm really disappointed with this upgrade...

---

### Post by howefield on 2016-08-22
You are not alone and the issue didn't originate with 16.04. If you feel like adding your weight to this bug, please do so.

[https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/1571913](https://bugs.launchpad.net/ubuntu/+source/pychess/+bug/1571913)

---

### Post by lou6 on 2016-08-22
Added to Launchpad.

---

### Post by howefield on 2016-08-22
Cool, thanks for that, I have done likewise.

Not sure I'd recommend it but the version from 14.04 appears to work in 16.04.1, don't mind on occasion installing packages from older repositories on my own machine but hesitate to do so for someone else for fear of unintended consequences. Version would need pinning so it isn't upgraded to the xenial package.

---

### Post by lou6 on 2016-08-22
I recommend Lucas Chess as an alternative (google it). It's a windows app but runs just fine with Wine 1.6.2 plus some winetricks tinkering.

---

### Post by SonnyE on 2017-01-23
Same problem. Solution: I went to the PyChess website and downloaded the latest deb package, which was pychess_0.12.4-1_all.deb

[http://www.pychess.org/](http://www.pychess.org/)

(In the process of doing that, there was another glitch that was sad. When I right clicked on the deb package for 12.4 in my Downloads folder and selected Software Install, Ubuntu Software Center showed the package information for version 12.2, which was the old installed version. Expecting brokenness is the norm, I clicked install anyway, and it did install the newer package that I had clicked on.)

---

