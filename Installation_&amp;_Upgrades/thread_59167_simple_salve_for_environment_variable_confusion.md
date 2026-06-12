---
title: "simple salve for environment variable confusion"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by Davec on 2005-08-23
I installed Ubuntu recently and loved it. For a while. Until I needed to add something to my path. Then it became horrible and confusing. 

I just found out about /etc/environment, and that makes a lot of sense, now that I know about it. But being human, and so not having ESP, I didn't find out about it without a bit of digging.

But there is a solution!  :D

/etc/profile should have a comment stating that changes to it will not take effect in Gnome sessions, as they would in almost any other distribution.

This is a simple fix which doesn't change any of Ubuntu's structure and which puts the documentation in front of people at exactly the moment that they need it.

Ubuntu is different, and different is good, as long as it's well documented.

---

