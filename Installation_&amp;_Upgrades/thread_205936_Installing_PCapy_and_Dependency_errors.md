---
title: "Installing PCapy and Dependency errors"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Maverynthia on 2006-06-29
I need to install PCapy to compile a script in order to stream music for this program. 
In order to compile PCapy I need GCC. I seems to be on my system, but I guess it's not so I go to add gcc4.0 Can't do that:
> gcc-4.0:
  Depends: gcc-4.0-base (=4.0.1-4ubuntu9) but 4.0.3-1ubuntu5 is to be installed
 Depends: cpp-4.0 but it is not going to be installed

OK so I'll just nuke gcc4.0-base out right...can't do that:
Fix broken packages first:
> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

So, I basically can't get this one script compiled because of all this...
What do I do?

---

