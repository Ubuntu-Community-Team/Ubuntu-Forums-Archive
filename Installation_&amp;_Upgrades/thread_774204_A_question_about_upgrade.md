---
title: "A question about upgrade"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by dr_cerebro on 2008-04-29
I'm using Ubuntu 7.10, I made a custom system, because several things do not work out of the box.

Update manager displays a message I can upgrade to Ubuntu 8.04 LTS.

If I upgrade (from update manager), all the customizations I did (ndiswrapper, custom DSDT, etc), are going to be lost?

---

### Post by Patsoe on 2008-04-29
> **dr_cerebro said:**
> I'm using Ubuntu 7.10, I made a custom system, because several things do not work out of the box.

Update manager displays a message I can upgrade to Ubuntu 8.04 LTS.

If I upgrade (from update manager), all the customizations I did (ndiswrapper, custom DSDT, etc), are going to be lost?

It's hard to say. Normally, the package manager does not overwrite configuration files that have been modified (or at least it's supposed to ask you for permission). If you changed other files that are in default locations (like under /usr/bin) then yes, these may be overwritten (however, /usr/local will be left untouched).

In the end, upgrading hundreds of packages is a complicated operation, and I wouldn't dare promise that your hand-made changes will be preserved. Only solution is to backup before upgrading.

---

