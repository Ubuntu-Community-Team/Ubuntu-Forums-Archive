---
title: "NOTE - if you installed e17 on hoary, your upgrade will have problems"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by reuben on 2005-10-15
If you put [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary in your sources.list a while back in order to try out e17, mplayer - among others - will not upgrade. 

To resolve: 

(In synaptic)
Try to upgrade mplayer
Note the dependency (the library) that it cannot install
Search by the library name (without the version)
Remove Full the version that is currently installed (it will take your old mplayer, plus all of the e17 cruft, with it)
Apply
Now try to upgrade mplayer again
This time it'll work

---

