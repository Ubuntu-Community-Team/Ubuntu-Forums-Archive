---
title: "libSM.so.6 shared liberary not found"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by SoFl W on 2011-01-04
Foolishly I ran "sudo apt-get autoremove"  (At least I think this is what caused the problem)  Now I see an error in session errors when I try and run pokerth.  

```
/home/SoFl_w/PokerTH-0.8/pokerth: error while loading shared libraries:
 libSM.so.6: cannot open shared object file:
 No such file or directory
```I have tried re-installing pokerth, but the current version is older and I don't think that will fix the problem.  If I type "libSM" into Synaptic package manager I am not sure which package I should make sure I have. libsm6 is installed.

Any ideas on how I can fix this?

---

### Post by SoFl W on 2011-01-05
I got some sleep and thought about this, where is the "apt-get" log? 
I will look at that and see what packages were removed and reinstall them.

EDIT:
I believe the problem is solved.  I went through the log and reviewed  the packages that "apt-get autoremove" deleted, adding them back one at a  time.  Finally after adding back "ia32-libs" (and whatever dependencies  it used) PokerTH started working again.

---

### Post by aaa bbb on 2011-07-21
Thanks your problem and answer helped me!

---

