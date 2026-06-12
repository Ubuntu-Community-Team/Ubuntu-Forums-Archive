---
title: "Missing Packages"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by spacemunkey on 2005-04-30
When trying to install fakeroot and kernel-package so I can compile my own kernel's i'm getting the following errors: I do have the universe repository enabled.

Reading package lists... Done
Building dependency tree... Done
Package kernel-package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-package has no installation candidate

Reading package lists... Done
Building dependency tree... Done
Package fakeroot is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package fakeroot has no installation candidate

---

### Post by jodef on 2005-04-30
You enable universe repository following the steps outlined in the : [Ubuntuguide - How to add extra repositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by spacemunkey on 2005-04-30
[QUOTE=jodef]You enable universe repository following the steps outlined in the : [Ubuntuguide - How to add extra repositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]

That worked. Apparently my .gnupg folder had become owned by another user. I rebuilt it then followed the instructions exactly and it worked. I also found out my sources.list was fubared.

---

