---
title: "Unable to upgrade from 18.04 to 20.04"
date: 2020-12-26
forum: Installation &amp; Upgrades
---

### Post by cobras on 2020-12-26
I'm running Ubuntu 18.04 on a Toshiba Satellite C55-A and trying to upgrade to 20.04.


 Software Updater first gives a "Failed to download repository  information" message but I continue on.  My internet connection is fine.   Then I get a notice that third party sources are disabled.

Then I get  404 errors.


 I've also tried the upgrade via the terminal and get the same results.
 
Thanks for any suggestions you can offer.

---

### Post by CelticWarrior on 2020-12-26
Where do you get the 404 errors? Meaning, what online destinations are giving the 404?

---

### Post by cobras on 2020-12-26
E:Failed to fetch [http://mirrors.sonic.net/ubuntu/dists/focal/main/source/Sources](http://mirrors.sonic.net/ubuntu/dists/focal/main/source/Sources)  404  Not Found [IP: 157.131.0.16 80], E:Failed to fetch [http://mirrors.sonic.net/ubuntu/dists/focal-updates/main/source/Sources](http://mirrors.sonic.net/ubuntu/dists/focal-updates/main/source/Sources)  404  Not Found [IP: 157.131.0.16 80], E:Failed to fetch [http://mirrors.sonic.net/ubuntu/dists/focal-backports/universe/source/Sources](http://mirrors.sonic.net/ubuntu/dists/focal-backports/universe/source/Sources)  404  Not Found [IP: 157.131.0.16 80], E:Failed to fetch [http://mirrors.sonic.net/ubuntu/dists/focal-security/multiverse/source/Sources](http://mirrors.sonic.net/ubuntu/dists/focal-security/multiverse/source/Sources)  404  Not Found [IP: 157.131.0.16 80], E:Some index files failed to download. They have been ignored, or old ones used instead.

Prior to this there was a notice about third party sources being disabled.

---

### Post by CelticWarrior on 2020-12-26
Change to another mirror and make sure the system is fully updated before trying again.

---

### Post by cobras on 2020-12-26
Thank you CW!  That was it.

I regularly check for updates and for months there had been none.  For this reason I finally decided to upgrade, figuring 18.04 was on the way out anyway.

With the new mirror there was a sheet load of updates to catch up on.

Funny thing, though, out of curiosity I ran a speed test before the upgrade but still on sonic.net and it seemed fine.

---

