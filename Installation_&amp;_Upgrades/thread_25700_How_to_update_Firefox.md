---
title: "How to update Firefox??"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-10
How do I upgrade Firefox on Ubuntu Warty? I can't find anything in synaptic and a  lot of extensions require at least Firefox 1.0 and I only have 0.9.3

---

### Post by jdong on 2005-04-10
Officially, once a release of Ubuntu is finalized, no updated packages are provided, except in the case of security fixes (where the specific fix is applied). If Ubuntu version X ships with Firefox version Y, it'll stay at version Y until the next release. this is done for stability reasons (Firefox 1.0 was unstable at the time, and Canonical decided not to mess with it!)


I started the Ubuntu Backports Project ([http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)) to provide package updates to the latest stable Ubuntu release. See the above link for information on adding the repositories (warty-backports, warty-extras) to your /etc/apt/sources.list.

I provide for Warty Firefox 1.0.2 (Hoary's latest verson recompiled against the Warty environment), among the 200+ other packages.

---

### Post by bigblop on 2005-04-11
Ok if I add these backports to my sources file should I just use apt-get install firefox to update firefox??

---

### Post by jdong on 2005-04-11
Correct; you may do an "apt-get dist-upgrade" to pull every applicable update found in Backports.


(For you "apt-get upgrade" fans, yes you do need **dist** upgrade to get Hotplug updates)

---

### Post by RU63 on 2005-04-12
Thanks so much for this thread.  I was worried when the old backport wasn't hitting anymore.  Now I am happy again. :)

---

