---
title: "alternate install disc doesn't install wireless drivers!!!"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by syxbit on 2007-03-08
This is really frustrating. I'm guessing it just doesn't install linux-restricted-modules.
I have trouble on my computer installing with the live disc, so I have to install via alternate, and then mess to get wired internet to work so that i can install wireless drivers.
what a pain

anyone else notice this?

---

### Post by mikewhatever on 2007-03-09
I am afraid non of Ubuntu installers install restricted modules. They are restricted (non free) and must be installed by the user. You can do it through the terminal
> sudo apt-get install linux-restricted-modules
If you have no wired connection, download the package for your kernel from 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all)

To check what your kernel is type uname -r in the terminal

---

