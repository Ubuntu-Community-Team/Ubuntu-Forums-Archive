---
title: "possible to install 2 copies of ubuntu?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by evencoil on 2010-04-30
I'm about to get a SSD to use as my / partition. I want to install another copy of Ubuntu on that drive which will coexist with my current installation until I have time to get the new installation exactly the way I want it (and then I'll get rid of the current installation).

I thought that this is probably possible and wouldn't be a problem, but I want to make sure. Is there anything I should watch out for?

---

### Post by oldfred on 2010-04-30
I have 3 Ubuntus, old install 9.04, current 9.10, & beta. I am still debating overwriting my 9.04 or keeping it one more cycle. I have not had to use it but it is the version I had upgraded from 6.10 ( or maybe 6.06 not sure).

I share data partitions and that has no issues between all the versions. 

The issue becomes /home. Once committed to the new version you should not use the old version if it is mounting the same /home as the older versions of all software may or may not work with the settings the new versions have written. Since most of my data is elsewhere my /home is small (about 1GB) so I may just copy it over to a new home.

In your case shared /home should be ok since the version is the same. Only if your test version installs things you do not want then you may have old settings saved.

---

