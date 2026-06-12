---
title: "Excluding kernel packages from installing"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by anzevi on 2006-09-21
Hello!

I have a 6.06.1 with 2.6.15-27-686 kernel running. I don't know why, but update manager wants also install kernel 2.6.15-27-386! :confused: 

How can i say to the package manager to EXCLUDE this stuff?

Thanks

---

### Post by SleepyHollow on 2006-09-21
Hi,

I have the same problem with this kernelpackage too. I'm using 2.6.15-XX-K7 but the update-manager also updates 2.6.15-XX-386.

How to exclude this update-stuff? I don't want to deinstall the installed 386er Kernel. Just want to keep it in case something is wrong with the K7-Kernel after an update.

Greetings
SleepyHollow

---

### Post by TheMono on 2006-09-21
Go into synaptic, and search for the package 'linux-image-386'. Select it, then click on the 'package' menu, and click lock version. That way it won't be upgraded.

That package is just a metapackage that depends always on the current kernel version, but locking that one *should* stop your 386 kernel from updating all the time... At least, it did for me.

---

### Post by SleepyHollow on 2006-09-22
> **TheMono said:**
> Go into synaptic, and search for the package 'linux-image-386'. Select it, then click on the 'package' menu, and click lock version. That way it won't be upgraded.


Cool, thanks it works. :D It's better to control the update-process. I don't like surprises. [-X

---

