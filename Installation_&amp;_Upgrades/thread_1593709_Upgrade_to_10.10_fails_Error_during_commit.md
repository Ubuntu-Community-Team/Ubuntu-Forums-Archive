---
title: "Upgrade to 10.10 fails: Error during commit"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2010-10-11
After downloading the packages I get the following error message:

"Could not install the upgrades

Error during commit
'E:Couldn't configure pre-depend X11-common for x11-xkb-utils,
probably a dependency cycle.'
Restoring original system state"

Any ideas what is the problem here and what can be done to solve it?

---

### Post by johann_p on 2010-10-11
Just saw that this seems to be a bug that is still in the final Ubuntu 10.10 release :(

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/639933](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/639933)

The solution suggested in comment #11 there worked to make the error go away.

---

