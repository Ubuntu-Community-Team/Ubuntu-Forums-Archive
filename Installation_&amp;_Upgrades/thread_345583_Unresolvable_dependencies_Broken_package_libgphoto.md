---
title: "Unresolvable dependencies: Broken package libgphoto2-2"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by Sciamano on 2007-01-24
Hi,
I'm trying to install the package libgphoto2-2-dev (which is required by f-spot 0.3.2) but I receive the following error:

```
The following packages have unmet dependencies:
  libgphoto2-2-dev: Depends: libgphoto2-2 (= 2.2.1-2ubuntu4) but 2.2.1.4.trunk-svn-r9304-0raof1 is to be installed
E: Broken packages

```

If I try to install via Synaptic, I receive the same message, but it specifies that the package has "unresolvable dependencies".
How can I solve?

Thanks

---

### Post by Sciamano on 2007-01-25
anyone? :(

---

### Post by Sciamano on 2007-01-25
Solved. Removed everything related to libgphoto and reinstalled everything. Now it works.

---

