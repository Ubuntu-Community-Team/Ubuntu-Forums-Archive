---
title: "apt-get install fails"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by dstew on 2008-02-27
I have a server install. I want to install the Ubuntu desktop. I used```
sudo apt-get install ubuntu-desktop
```Almost all the package files downloaded but there were a couple that did not. I got 402 errors for those. I assume that there might have been a server problem (this was Sunday after all) so I figure they will get it sorted by Monday evening.

I would like to finish the installation without having to download all the other packages again. So, do I do **apt-get install ubuntu-desktop**, or **apt-get install -f ubuntu-desktop**? Is apt-get smart enough to know that it has almost all the packages in the cache, and that it only needs to get a few more?

---

### Post by fedex1993 on 2008-02-27
um one thing is the repos might be disabled to install like that stuff but i dought it

---

