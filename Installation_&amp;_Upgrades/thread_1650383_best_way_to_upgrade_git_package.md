---
title: "best way to upgrade git package"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by deesto on 2010-12-21
I'm running 10.10 with the latest (safe) updates.  Unfortunately for me, this release includes a very buggy version of the `git` client for my purposes (v1.7.1).  I'd like to upgrade this to a more modern version, but I can see from the Ubuntu packages page that the sheer number of dependent and related packages could make things a bit messy:
[http://packages.ubuntu.com/maverick/git](http://packages.ubuntu.com/maverick/git)

This may be more of a question on bleeding-edge packages than on one specific package, but I'd like to know the recommended method for upgrading specific packages to something newer than the canonical version (is this just adding a repo? I see that Natty already has a better 1.7.3.2 version)?  And once this is done, is this something that can still be maintained by aptitude?

---

### Post by gmargo on 2010-12-21
There's a ppa for the latest stable git:
[https://launchpad.net/~git-core/+archive/ppa]("https://launchpad.net/%7Egit-core/+archive/ppa")

---

### Post by deesto on 2010-12-21
Great; thanks gmargo.  I can't add repositories using **apt-add-repositories** because I'm behind a proxy+firewall and the tool doesn't seem to like that, but this is another issue entirely.

---

