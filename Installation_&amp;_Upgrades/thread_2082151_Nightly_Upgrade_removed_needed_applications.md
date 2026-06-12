---
title: "Nightly Upgrade removed needed applications"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2012-11-08
Last evening's update removed /usr/bin/komposer from my computer.
I needed and regularly use that application to maintain a web page.

This is not the first frequently used application that Ubuntu upgrades
have silently and covertly removed from my computer.

---

### Post by Frogs Hair on 2012-11-08
Was this an update or upgrade ? If an upgrade to a new version of Ubuntu the software may no longer be computable. Packages are sometimes removed from the repository for the same reason and it is the developers responsibility to maintain them . The package system will remove any conflicting packages.

---

### Post by oldos2er on 2012-11-08
> **arvevans said:**
> Last evening's update removed /usr/bin/komposer from my computer.

Which version of Ubuntu are you using?

---

### Post by arvevans on 2012-11-09
After locating and re-installing the missing software it appears to work perfectly, so non-operability in Ubuntu 12.10 does not seem to be an issue.

I recently did a distribution upgrade from Ubuntu 12.04 to Ubuntu 12.10, but the missing software seems to have gone away due to an automated package list *update* and package *upgrade* within release 12.10.

When I did the distribution upgrade from Ubuntu 12.04 to Ubuntu 12.10 there were other software packages that disappeared, but pointers to the needed packages were provided by individuals here on the forum and the removed packages were re-installed and are working with no problem.

This is all a minor irritation, but it does seem to imply that builders of the update & upgrade processes need to take a closer look at what is being done to users who already have working systems that use specifically needed software applications.

---

### Post by QIII on 2012-11-09
They were likely not covertly removed.  More likely you were offered a partial upgrade, which sometimes happens when packages and dependencies don't hit the repo at the same time.

In both the GUI and in the terminal, you will often see "The following packages will be removed:".  If you see that, either don't upgrade until all the packages are in place or use dist-upgrade to have the process try to intelligently resolve dependency issues.

The key is for the user to pay attention.  Developers don't always know whether or not a dependency common to several packages has been put in the repo.

---

