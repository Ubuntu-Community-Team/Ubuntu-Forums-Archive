---
title: "Scipy and Numpy incompatibility"
date: 2020-11-16
forum: Installation &amp; Upgrades
---

### Post by kwiesen on 2020-11-16
Hi, I'm new to Ubuntu.   I'm using a distribution of 18.04 LTS that has python 3.6.9, numpy 1.18.1 and scipy 0.19.1.    When I try to use the butter module from scipy.signal I get  [COLOR=#0000ff]ModuleNotFoundError: No module named 'numpy.testing.nosetester[/COLOR]'.  This is apparently due to the deletion of this module from numpy 1.18.   So the main problem seems to be that scipy version 0.19.1 is 3 years old while numpy 1.81.1 is quite recent.   However, when I try to update scipy using apt or apt-get it tells me  [COLOR=#0000ff]python3-scipy is already the newest version (0.19.1-2ubuntu1)[/COLOR].   When I try to upgrade scipy via pip3 there are lot of other dependencies that come up and it is quite painful.  I was able to downgrade my numpy to version 1.17.5 which seems to have fixed my immediate problem.   My question is why are the scipy and numpy versions that come with this distribution so far out of sync and why does apt-get think scipy 0.19.1 is the latest version?   Was there a better solution to my problem than downgrading numpy?

I couldn't find any helpful links on this issue.   Any help or advice is greatly appreciated.

---

