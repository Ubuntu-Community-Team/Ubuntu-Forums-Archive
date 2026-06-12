---
title: "apt-get, how to upgrade beyond current and still upgrade later?"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by scottlindner on 2008-08-30
I'm running Ubuntu 8.04 and the latest version of SquirrelMail that I can get with apt-get.  There is a fix that I need that is in version 1.4.16 on the SquirrelMail site.  I know it takes time for these things to make it into the baseline for Ubuntu.  Is there a way to download and install the latest version on the SquirrelMail site and still preserve the functionality with apt-get?  What I mean is to preserve the dependency checking, and when Ubuntu does catch up and move beyond 1.4.16 so I can use apt-get to upgrade?

My concern is if I download it and install it manually all bets are off going forward.

Cheers,
Scott

---

### Post by gjoellee on 2008-08-30
yes, but if the fix isen't in the repo, nothing will happen. It often takes time before new verisons of software gets out in the repo... So just try and see if there is a new version :)

---

### Post by forger on 2008-08-30
You could also try the package from the development release of ubuntu [http://packages.ubuntu.com/intrepid/squirrelmail](http://packages.ubuntu.com/intrepid/squirrelmail)
(click on "All" link and choose a download mirror)

No guarantees though

---

