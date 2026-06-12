---
title: "Problem with Moblock update"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by gingin on 2007-07-11
Platform Feisty Fawn (7.04)
**Does anybody have got such optimistic message during moblock update?**

I have reinstalled   libc6 and libnetfilter-queue1. 
But terminal still do not trust me as I did and reworded with following stuff:  
[I]The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.13) but 0.0.12-1 is to be installed
               Depends: libnfnetlink0 (>= 0.0.25) but it is not installable
E: Broken packages [/I]

Sypmatic manager couldn't fide  libnfnetlink0....

Is it same thing can be don to correct this?

---

### Post by catfishy on 2008-01-01
I have the same problem, nothing at all can update because of this moblock problem.  I can't remove it, update, or anything!  I'll keep searching for a solution.  Good luck!

---

### Post by jre on 2008-01-01
Plz verify that you have the correct sources.list entry:
```
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) **feisty** main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) **feisty** main
```

To remove:
aptitude purge moblock-nfq

Note: I propose to use "moblock-nfq" currently. The "moblock" package contains newer code but is still in a testing stage.

---

