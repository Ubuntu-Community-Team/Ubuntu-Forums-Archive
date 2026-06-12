---
title: "Problem with NetworkManager and DSL"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rudenko_ruslan on 2009-08-07
Hello.

After recent updates of "[network-manager]("https://lists.ubuntu.com/archives/karmic-changes/2009-August/005824.html")" and "[network-manager-applet]("https://lists.ubuntu.com/archives/karmic-changes/2009-August/005825.html")", my DSL connection has been broken. NetworkManager tries to connect at startup, but no luck.

NetworkManager Applet is in unusable state right now, so I'm forced to use pppoeconf.

Have anyone encountered with this problem too?

---

### Post by rudenko_ruslan on 2009-08-19
Problem solved after using [NetworkManager's Trunk PPA]("https://edge.launchpad.net/~network-manager/+archive/trunk") from [asac's site]("http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html").

---

