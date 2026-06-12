---
title: "Unmet dependecies"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by LordSmugger on 2011-07-03
I've been trying to upgrade from 10.10 to 11.04 since Natty was released. Every time I try to upgrade I get the same error: ```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
```

So, in searching around, I've discovered sudo apt-get -f install. Which nets this: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 apturl : Depends: apturl-common (= 0.4.1ubuntu7.1) but 0.4.2ubuntu5.1 is installed
 apturl-common : Depends: python (>= 2.7.1-0ubuntu2) but 2.6.6-2ubuntu2 is installed
 kdelibs5-plugins : Depends: kdelibs5-data (= 4:4.6.2-0ubuntu4.1) but 4:4.5.5-0ubuntu2 is installed
 kdoctools : Depends: kdelibs5-data (= 4:4.6.2-0ubuntu4.1) but 4:4.5.5-0ubuntu2 is installed
 python : Depends: python-minimal (= 2.6.6-2ubuntu2) but 2.7.1-0ubuntu5 is installed
 python-kde4 : Depends: python (>= 2.7) but 2.6.6-2ubuntu2 is installed
 python-twisted-names : Depends: python (>= 2.7.1-0ubuntu2) but 2.6.6-2ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

I'm curious as to how I'll correct these "held packages" and fix/ (or upgrade) any broken dependencies.

---

### Post by LordSmugger on 2011-07-05
Well, since it's been a couple days, and I finally got upgraded to 11.04, I'm going to mark this thread as solved.

In case anybody is wondering, I managed to do a clean install of 11.04, even though all I wanted was an upgrade.

---

