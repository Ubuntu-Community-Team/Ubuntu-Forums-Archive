---
title: "aptitude broken packages"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by The_Boss on 2007-02-27
Somethings been bugging me about aptitude lately.  I like to keep my packages nice and tidy, so I've been starting to use command-line aptitude to search for any problems in my repository.  

I started using this command: "aptitude search ~c" which shows me packages which are no longer installed, but still have configuration files on my system.  I don't see any reason to keep those around, so I'll usually go ahead and purge those.  Now I toss aptitude another interesting search parameter:  "aptitude search ~b" which is supposed to show me a list of broken packages.  It spits out a list of about 12 packages, all have the "i" flag for "installed", and "B" flag which I'm assuming means broken.  The interesting thing is that if I'm doing an upgrade or dist-upgrade, aptitude only reports one of these packages as broken, not complaining about the others.  What it'd like to know is:

1)  Are these other packages with the "B" flag actually broken?
2)  If so, how can I easily tell in which way they are broken (suggests, depends, conflicts, recommends, etc)
3) So when I'm doing an upgrade/dist-upgrade, is aptitude only complaining about broken "recommends" dependencies?

---

### Post by bapoumba on 2007-02-27
Hello :)
Open ```
aptitude
``` in a terminal and search for broken packages. When a package is highlighted, hitting **e** will examine the situation (and tell you why it is broken) and propose some actions.

---

### Post by The_Boss on 2007-02-27
Thanks!  That at least lets me see the reason why it's claiming those packages are broken.  I guess it's expected that some things will be broken for me in the feisty-dev branch :-)

Is there any way to this (ie examine why a package is broken) simply using command line aptitude?  "aptitude show <package-name>" displays all of a packages suggests, recommends, depends,etc but it doesn't highlight what's currently missing.

---

### Post by bapoumba on 2007-02-27
> **The_Boss said:**
> Thanks!  That at least lets me see the reason why it's claiming those packages are broken.  I guess it's expected that some things will be broken for me in the feisty-dev branch :-)

Is there any way to this (ie examine why a package is broken) simply using command line aptitude?  "aptitude show <package-name>" displays all of a packages suggests, recommends, depends,etc but it doesn't highlight what's currently missing.

You're welcome.
Not sure it can do exactly the way you asked, but you can search with ~Btype, where *type* is the type of dependency:
> ~Btype

    Matches packages which have an unfulfilled (“broken”) dependency of the given type. type can be “depends”, “predepends”, “recommends”, “suggests”, “conflicts”, or “replaces”. 
[http://people.debian.org/~dburrows/aptitude-doc/en/ch02s03.html]("http://people.debian.org/~dburrows/aptitude-doc/en/ch02s03.html")
[http://people.debian.org/~dburrows/aptitude-doc/en/rn01re01.html]("http://people.debian.org/~dburrows/aptitude-doc/en/rn01re01.html")

---

### Post by The_Boss on 2007-02-28
thanks, the ~Btype option is pretty useful.  At the very least I can do an "aptitude search ~i~Bsuggests" for example, and then individually do an "aptitude info packagename" on each of the packages that comes up in the previous search and look at the "suggests" category for example for missing packages.  

I wish I could somehow get command-line aptitude to consistently print out information like "Package A suggest package B, but package B is not installed", but it doesn't seem to do that for some of the packages that come up during a ~b query :-(

---

