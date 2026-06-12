---
title: "Urgent Upgrade"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Peterfc on 2008-05-07
On release day i upgraded to Ubuntu 8.4 and all worked well. I now have an important security update .

I get the messages i have pasted below. Can anybody help this newbie. Thanks for all who looked at this post

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



Version 4:3.5.9-0ubuntu7.1: 

  * SECURITY UPDATE: integer overflow in start_kdeinit. The start_kdeinit
    processing of user-influenceable input is faulty.  A local user
    might be able to send unix signals to other processes, cause
    a denial of service or even possibly execute arbitrary code.
  * Add kubuntu_9903_kinit_integer_overflow.diff, edits
    kinit/start_kdeinit.c, patch from upstream KDE
  * References
    [http://www.kde.org/info/security/advisory-20080426-2.txt](http://www.kde.org/info/security/advisory-20080426-2.txt)

---

### Post by Tomatz on 2008-05-07
Just do as the error message asks.


In a terminal:

```
sudo dpkg --configure -a
```

then

```
sudo apt-get update
```

(just for good measure)

Then try to update/upgrade again ;)

---

