---
title: "failed to start upgrade 13.10-14.04"
date: 2014-10-16
forum: Installation &amp; Upgrades
---

### Post by computermike on 2014-10-16
Kubuntu (but also runs Unity- Unity on the main console, KDE on remote sessions) on i5 processor. At the second stage (new channels) a window pops up to say that either I am upgrading to or from a pre-release version, or there is a problem with some application that did not come from Ubuntu. As far as I am aware there are no packages that are not from Ubuntu or reasonably common, that have survived other upgrades. The only one that could be suspicious is virtualbox, which has a windows and a macos installed. Unfortunately this error message gives me no hint as to what is actually causing the problem. I do not want to try uninstalling everything until I find the right one, it would be simpler just to start afresh with a different OS! Is there any way of telling exactly what is causing the problem, so that I can just uninstall that, upgrade and then reinstall?

Mike

---

### Post by grahammechanical on 2014-10-16
Your experience and the experiences that others have had are the reasons why some of us recommend a fresh install of a newer version instead of upgrading. To avoid failures I would revert the OS back to the default as much as possible. I would have a default theme and the open source video driver. 

Your set up is more complicated than a default install. You can run

```
sudo apt-get update
```

and note the repositories that are being accessed. You may find in the list of URLs some Person Package Archives (PPA) or a URL to some other software repository. The updater/upgrader utility cannot determine the exact cause of the problem. So, the error message covers a range of possibilities.

You may also need to consider the fact that is is now almost a year since 13.10 was released and it only had 9 months support. So, you may be in the position of doing an End of Life upgrade. 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Big changes are coming to Ubuntu over the next 18 months. So, unless we are willing to accept a bumpy ride and upgrade/fresh install every 6 or 7 months, then I suggest we get to 14.04 and stick with it until 16.04 is released.

Regards.

---

