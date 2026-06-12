---
title: "2 n00b questions regarding repositories from a gentoo &amp; debian user"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by biggerben on 2006-05-13
hi everyone
i've just installed breezy for my sister on her laptop (windows wasn't working properly :-D )
I'm a gentoo user, and i can't figure out how to do certain things in ubuntu:

[LIST]
[*]breezy has amsn 0.94. how do i install the newer version of amsn (0.95) (which came out in 2005!) through apt? is there no such thing as **ACCEPT_KEYWORDS=~x86 apt-get install amsn**, or **apt-get install amsn-0.95** or **BRANCH=unstable apt-get install amsn**? is it possible to install msn from the drapper repository? oh, and how come a version released in 2005 hasn't made it into breezy yet?

[*]before gentoo i used debian briefly (before ubuntu was around!). there you could select between the repositories woody, sid, sarge (which would all turn old (stable) and get very outdated, OR (which i chose) you could select stable, testing, unstable. debian unstable for example would always be up to date, and still will be even when sid turns stable. is that the same in ubuntu, or do you just have to 'manually upgrade' to drapper and edgy when they come out?
[/LIST]

I tried to find this through help.ubuntu.com, but they only seem to address more basic problems there!

any help appreciated!


-Ben

---

### Post by aysiu on 2006-05-13
If you want aMSN 0.95, use [this script](http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47) to install it.

Ubuntu's repositories get updated every six months with new releases. Sometimes certain packages will be updated before that for security reasons or just because someone put an updated package in the backports. Otherwise, Dapper comes out officially in three weeks...

---

