---
title: "Software upgrade shuts computer off immediately"
date: 2016-05-11
forum: Installation &amp; Upgrades
---

### Post by aajax on 2016-05-11
When attempting to use Software Upgrade some errors were encountered to the effect that a package failed.  One of these advised running the command "apt-get install -f" which I did.  Software Upgrade seemed, for a while, to be in the deadly embrace.  In that, when invoked it appeared to start over searching for applicable upgrades and then reproducing the same list.  Eventually, choosing "Installation" resulted in having the computer turned off.  I say turned off rather than shutdown because it happens very fast.  Much faster than shutdown would take.  Now the computer is in a state where any attempt to start the the Software Upgrade turns the computer off.

The version of Ubuntu is 14.04.4 LTS
The computer is a Dell Laptop (Latitude D810)

Is there some way to recover which doesn't involve the need to use the Software Updater?

---

### Post by ian-weisser on 2016-05-12
Ubuntu does not have a super-fast-shutdown mode.
Are you really sure you are not encountering a hardware problem triggered by the intense disk, memory use, or corresponding extra heat or power draw?

If you are sure that the problem is software, then please open a terminal and show us the complete output of the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```

---

