---
title: "is it possible to cancel upgrade to 11.04?"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by bamibestelt on 2011-09-18
guys, this might be silly though...

recently, i tried to upgrade my maverick ubuntu to 11.04
but somehow, when I download the package etc, the process stop
and said "there might be error with ur internet connection" (kind of it) and then I tried again, but the error is still occur...

now, for couple of days I decided not to upgrade my ubuntu instead I will stay in my current version 10.10

however, something annoying me when the update manager keep popping me that I should run PARTIAL UPGRADE in order to complete the upgrade...

What should I do to stop this?
Any idea would be grateful! thanks ;)

---

### Post by zvacet on 2011-09-22
What is output of 

```
lsb_release -a
```

and if you are still running 10.10 

```
sudo apt-get update && sudo apt-get upgrade
```

Post output here.

---

