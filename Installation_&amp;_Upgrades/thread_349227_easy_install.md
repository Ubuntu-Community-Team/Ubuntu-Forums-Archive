---
title: "easy_install"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by xinman on 2007-01-29
Hi,

First off I'm running breezy.  I am trying to install webadmin for trac and it comes in "egg" format?  Which needs easy_install to install it.  I've installed python2.4-setuptools but I still cannot run easy_install, I've look all over the place and there is no easy_install on my system.  Can someone please help me, I've never really done much with python so this is all new to me.

Thanks,
Dan

---

### Post by wolfear on 2007-07-20
I realize this is a bit late, but it may help someone else:
I'm running 6.06 server and the version of setuptools in the repos will not (as far as my recent encounter with it goes) work with recent versions of Trac.
I had to use [http://peak.telecommunity.com/DevCenter/setuptools]("http://peak.telecommunity.com/DevCenter/setuptools")

This may just be an issue with my system, but that was the only version that I could find which worked.

At the time of writing this, the link used by the repos version pointing to python.org is not functioning and the other link (can't remember the website name) found on the Trac website is also dead.

Maybe this will save someone else some head pounding.

---

