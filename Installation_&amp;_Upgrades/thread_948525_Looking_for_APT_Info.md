---
title: "Looking for APT Info"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by gamechampionx on 2008-10-15
I've really been enjoying Ubuntu, and I'm rather interested in apt-get.

I recently found out that you can specify <package>=<version> which is neat, hoping update has a similar option (or perhaps install will overwrite the previous one?).  I have a lot of questions regarding that functionality and other related topics and I'm wondering if there are any cohesive documents about it.

I'm really interested in the algorithm is uses for managing dependencies.  For example, does it in general update package dependencies to the latest-greatest even if the dependency is satisfied by what is already installed?  I read somewhere that solving this problem elegantly is in fact NP-complete which makes me wonder.

Any help is appreciated.

---

### Post by mssever on 2008-10-16
> **gamechampionx said:**
> I've really been enjoying Ubuntu, and I'm rather interested in apt-get.

I recently found out that you can specify <package>=<version> which is neat, hoping update has a similar option (or perhaps install will overwrite the previous one?).  I have a lot of questions regarding that functionality and other related topics and I'm wondering if there are any cohesive documents about it.

I'm really interested in the algorithm is uses for managing dependencies.  For example, does it in general update package dependencies to the latest-greatest even if the dependency is satisfied by what is already installed?  I read somewhere that solving this problem elegantly is in fact NP-complete which makes me wonder.

Any help is appreciated.
I don't know if I can answer all of your questions, but I'll give it a shot. Note that I use aptitude rather than apt-get, so some of what I say might not apply to apt-get.

When you install a package, aptitude only installs other packages to satisfy dependencies. Aptitude by default considers recommended packages as dependencies, while apt-get and synaptic don't. If you have an older version of a package installed, but it satisfies the dependency, then installing another package won't upgrade it. You'll need to either do an upgrade, or explicitly name the package in the install command. Unless you specify a version to the contrary, if you have foo-program version 1 and version 2 is available, then saying "sudo aptitude install foo-program" will upgrade to version 2.

---

### Post by gamechampionx on 2008-11-23
The info you gave me was certainly helpful.

I've got a few followup question if you don't mind:

1. Does the "latest-greatest" idea extend to packages installed only to satisfy dependencies?  I.e. does the minimum version get install or the newest in satisfying dependencies?

2. How does uninstall work?  Does it handle removing packages only used to satisfy dependencies?

Thanks a ton.

---

### Post by mssever on 2008-11-24
> **gamechampionx said:**
> 1. Does the "latest-greatest" idea extend to packages installed only to satisfy dependencies?  I.e. does the minimum version get install or the newest in satisfying dependencies?The latest version in one of your repos is always installed unless you specify something different or unless a package installed depends on a specific version of some other package.

> 2. How does uninstall work?  Does it handle removing packages only used to satisfy dependencies?Depends. If you use aptitude to install packages, then dependencies are marked as auto-installed. Auto-installed packages get removed when nothing depends on them. I think that apt-get and synaptic work the same as of Intrepid, but I'm not certain. At any rate, to explicitly mark a package as autoinstalled, use +M. E.g., ```
sudo aptitude install libfoo+M
``` will install libfoo if it isn't already installed and mark it as autoinstalled in any case.

---

