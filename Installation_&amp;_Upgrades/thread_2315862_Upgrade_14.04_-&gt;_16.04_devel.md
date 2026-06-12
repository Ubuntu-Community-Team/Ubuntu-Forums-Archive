---
title: "Upgrade 14.04 -&gt; 16.04 devel"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by andr16 on 2016-03-03
Hi,

I keep getting error messages when trying to run "do-release-upgrade -d" on my 14.04.4 LTS"
From the logfiles I could identify the following issues:

apt.log:  module-init-tools:amd64 Depends on libkmod2 [ amd64 ] < 15-0ubuntu6 -> 22-1ubuntu1 > ( libs ) (= 21-1ubuntu1) can't be satisfied!
main.log:2016-03-03 09:50:26,770 ERROR Unauthenticated packages found: 'module-init-tools'

Maybe waiting two more months would solve the problem, but I just can't......

---

### Post by grahammechanical on 2016-03-03
Do a fresh install of 16.04 from a daily ISO image.

I have been running the development version of Ubuntu for about 3 years. I use it as my daily Ubuntu. When a new version of Ubuntu is released I put in a fresh install of it and then I upgrade it to the development version of the next release of Ubuntu. I do that within the first 4 weeks of the start of development period. That is when the code differences between the two versions are small enough not cause great problems.

After the first 4 weeks of a development period I would not upgrade from the previous version. The code differences are then too great for there not to be a risk. We must be about 18 weeks into the 26 week development period of 16.04. Think of the changes that have been made to what was 15.10 to get to where Xenial Xerus is now. And it is still not 16.04.

If I wanted to test the upgrade path from 15.10 or 14.04 to 16.04 then I would do that during the last 4 weeks of the development period. That is when the developers have sorted out what needs to be done for when users upgrade to 16.04.

In between the fourth week and the twenty-second week of the development period I would advise putting in a fresh install of a daily ISO image and not trying to upgrade.

Regards.

---

### Post by andr16 on 2016-03-03
Many thanks for the answer! Very good to know! So I'd wait until the release since cuz a clear install would just delete all my other tools and software.

---

### Post by Bucky Ball on 2016-03-03
Yes, best to wait for release. Unsure why would want to go from a stable and supported LTS release to a development version at this point. :-k

---

