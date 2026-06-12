---
title: "package system blocks"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by jonasg on 2007-09-22
Hey,

I've installed some 3rd party packages to make my Canon camera work with ubuntu. The packages were compiled for fiesty using gutsy source if I remember correctly. But now each time I use apt-get or any kind of GUI packaging interface I get the following errors:

```


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing linux-restricted-modules-2.6.10-6-386 (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

```

---

### Post by Pumalite on 2007-09-22
Try this:

sudo dpkg --configure -a

Report back.

---

