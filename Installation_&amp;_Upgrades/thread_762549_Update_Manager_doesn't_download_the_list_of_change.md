---
title: "Update Manager doesn't download the list of changes"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by manuquadros on 2008-04-22
Update Manager is working fine, except for one thing: although I can get the latest updates, I can never see the lists of changes. It always shows:

> Failed to download the list of changes. 
Please check your Internet connection.

Does any one know why?

By the way, I'm using Ubuntu 8.04

---

### Post by wpshooter on 2008-04-22
I have seen this problem on previous versions of Ubuntu.

Seems like to me that I tried completely reinstalling the O/S but to the best of my recall that did not fix the problem.  Seems to me that I had to wait for a fix to come along for the problem to be resolved.  

I think that this is probably a bug in the NEW Hardy version.

Why don't you do a bug report on it.

Good luck.

---

### Post by Jack Brown on 2011-06-19
hi i know this thread is in a coma.

but since 
- it's not marked solved
- issue / bug still occurs
- this thread is one of the first relevant results in good ole search engine

it's now AWAKE.  (two, now three posts shouldn't matter much right)

ok you if the above (thread title) happens, you could try 
$sudo apt-get update on the terminal..  

and changelog should appear again.

(unless it was the couple of reboots that solved it)
either can be tried.

happy bunt to u

---

### Post by peterhoeg on 2011-08-18
There are 2 things going on here:

1) If you do not have 'apt-listchanges' installed, it will not work, and

2) There is a known bug with kpackagekit and apt-listchanges in natty:
[https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/803369](https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/803369)

So the short version is - it doesn't work yet.

> **Jack Brown said:**
> hi i know this thread is in a coma.

but since 
- it's not marked solved
- issue / bug still occurs
- this thread is one of the first relevant results in good ole search engine


---

### Post by Elfy on 2011-08-18
closing old thread - start a new one of you need support

---

