---
title: "breezy badger (5.10) server install -- aptitude update fails"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by bigbuck on 2007-07-09
Hi folks,

I have had Ubuntu 5.10 (breezy badger) installed for some time, and have done regular maintenance updates.  However, in the past couple days, I have not had any luck, and am always getting the following when I try to do an update prior to an upgrade:

root@machine:~# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
root@machine:~#

Is it possible that this distribution is too old now?  Is doing a dist-upgrade a safe option for me (I ask only because I have heard that there were numerous problems, and I have been happy with the stability of this version thus far).  If it's safe to upgrade, which version should I choose, and what is the procedure to get there, given that it appears the current sources are no longer available?

Thanks,

bb.

---

### Post by tgm4883 on 2007-07-09
> **bigbuck said:**
> Hi folks,

I have had Ubuntu 5.10 (breezy badger) installed for some time, and have done regular maintenance updates.  However, in the past couple days, I have not had any luck, and am always getting the following when I try to do an update prior to an upgrade:

root@machine:~# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
root@machine:~#

Is it possible that this distribution is too old now?  Is doing a dist-upgrade a safe option for me (I ask only because I have heard that there were numerous problems, and I have been happy with the stability of this version thus far).  If it's safe to upgrade, which version should I choose, and what is the procedure to get there, given that it appears the current sources are no longer available?

Thanks,

bb.

It is too old, the necessary stuff that you need has been removed.  You need to upgrade, but i'm not sure about what the best method for you is.

---

### Post by bigbuck on 2007-07-09
This seems somewhat like Microsoft suddenly yanking their updates for Windows off their site...they normally give users reasonable notice that an OS is being end-of-lifed, and even then, they just stop adding new updates, the old ones are still available for people to use.  In this case, whether notice was given or not, I don't know, certainly I wasn't aware of it, but nevertheless, I would have at least hoped for the updates that existed to remain in existence.  It's not like disk space is expensive these days, and had I known it was going to go away, I simply would have archived all of it to allow me to at least point my server at the copied repository to allow me to continue down the same path for a while until such time as I could come up with the time and a game plan to move ahead.

Lest someone mistake this post as wanting to fuel the Windows vs. Linux argument, let me point out that I still have Solaris 7 (also an old OS) for which I can still get patches from Sun.  This is not a pro-MS rant, but it seems only the Linux camp has still not come to grips with the fact that can't put something out there one day and then just yank it back the next.  Clearly, since both SuSE (at the time before they were Novell) and now Canonical have done this to me, I've made a mistake in thinking I could trust Linux for the stability and reliability of running my main servers.

Despite the fact that Linux folks are always talking about lowering the total cost of ownership, it seems I've spent more time replacing my Linux OS in the last five years than I've spent replacing either Windows or Solaris.  I don't want this thread to get away from the original reason of looking for a way forward from my current problem, but perhaps someone can (at the same time) explain to me why the sudden removal of these sources is beneficial to anyone?

Thanks,

bb.

---

### Post by tgm4883 on 2007-07-09
I can't say that it is beneficial.  Although I would point to that the end of life was in April.  (I believe it is 18 months for regular releases. 3 Years for LTS Desktop edition, and 5 years for LTS Server edition).  They didn't remove these immediately allowing people to backup, upgrade, and so forth.  5 years is a long time between upgrades, and I can justify to myself doing the work required to upgrade after that many years.

That being said, I see no reason to remove it, other than it was end of life, possilbly required upkeep.

---

