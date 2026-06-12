---
title: "Will python easy_install conflict with dpkg?"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by Cowloon on 2008-01-26
If I use easy_install will the files that are installed conflict with python and other packages installed via dpkg?

---

### Post by yabbadabbadont on 2008-01-26
The definitive answer is....  maybe.  ;)

It just depends upon what the package you are installing with it actually installs.  If it is a good little package and doesn't overwrite any other package's files, then you should be fine.  The problem is that you probably have no way of knowing before you install it, if it will overwrite anything...  stick to the software in the repositories if possible.  If you can't find it there, make sure that you have all of the repositories enabled.  Also, it might help if you told us which package you are thinking about installing.  Someone may be able to point you to a deb that you could install with dpkg instead.

---

### Post by Cowloon on 2008-01-26
I wanted to install pylons and related things. The versions in the repository are slightly older than the versions in tutorials that I'm looking at.

How about this, where is easy_install going to install things? Can I have it install things into a different place then where dpkg would install things?

---

### Post by yabbadabbadont on 2008-01-26
Sorry, no clue.

---

