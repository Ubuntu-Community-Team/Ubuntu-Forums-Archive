---
title: "Simple Q: Where is sendmail?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by babzog on 2010-01-09
Just got my VPS provisioned with ubuntu9.04 (64bit) and am trying to get it configured correctly.  Part of that means I need sendmail.  I've been using aptitude to install software but sendmail is nowhere to be found.  Even running 'aptitude install sendmail' results in nothing but "No candidate version found for sendmail".  Similar for apt-get.

Suggestions for where to go from here?  I wonder what other software might be hidden or not available?

Cheers!

---

### Post by babzog on 2010-01-10
Any suggestions where to go from here?

---

### Post by babzog on 2010-01-23
I guess noone here uses sendmail, huh?  

It turned out to be a problem with the source.list, post-install.  Who knew that there were other repositories of software like universe, multiverse, etc.  Certainly not this ubuntu-newb. ](*,)  Once I was informed of their existence and plugged them in, I was able to install.

Thanks for all the helpful advice!  :popcorn:

---

