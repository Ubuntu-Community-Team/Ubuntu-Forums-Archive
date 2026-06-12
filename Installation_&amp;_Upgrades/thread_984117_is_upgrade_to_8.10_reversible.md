---
title: "is upgrade to 8.10 reversible?"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by palika on 2008-11-16
I wish I didn't upgrade to Intrepid. I lost tons of applications, libraries, settings, you name it. E.g. my TV tuner card is no longer recognised, games will not start (they did before), the archive manager is crapping out all the time, downloads and package installs hang, even with synaptic. I'm frustrated and frankly pissed.
E.g. i keep getting the following error message, when trying to start an app in a terminal window, whther as root or not:

error while loading shared libraries: libopenal.so.0: cannot open
> shared object file: No such file or directory

Is there any way to go back to 8.04 (like a system restore in Windows)?

---

### Post by iponeverything on 2008-11-16
> **palika said:**
> I wish I didn't upgrade to Intrepid. I lost tons of applications, libraries, settings, you name it. E.g. my TV tuner card is no longer recognised, games will not start (they did before), the archive manager is crapping out all the time, downloads and package installs hang, even with synaptic. I'm frustrated and frankly pissed.
E.g. i keep getting the following error message, when trying to start an app in a terminal window, whther as root or not:

error while loading shared libraries: libopenal.so.0: cannot open
> shared object file: No such file or directory

Is there any way to go back to 8.04 (like a system restore in Windows)?

As far as backing out -- for most mortals it is not possible. Backup and your data reinstall your previous version.

---

### Post by agentsmith23 on 2008-11-19
To fix the error you are receiving install this:

[http://mirrors.kernel.org/ubuntu/pool/universe/o/openal/libopenal0_0.2005080600-2.1build2_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/o/openal/libopenal0_0.2005080600-2.1build2_i386.deb")

It fixed the same problem for me!

---

