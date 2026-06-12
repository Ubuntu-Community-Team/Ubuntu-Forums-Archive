---
title: "Failure when installing Crossover"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by eg-maverick on 2007-01-24
When I try to install crossover, the archive integrity checks ok, the uncompress is ok. I get a warning and then a failure. The warning message is:
"The DISPLAY variable is not set. You should either login to as root or use the command "su" with no flags, to make sure setup has an X display to use."

What does that mean and what should I do about it?

the failure message is:

"The setup program seems to have failed on x86/glibc-2.4"

I checked Synaptic and there is no glibc but I don't again know exactly what to look for. I am running 6.10.

Thanks,
Craig

---

### Post by taurus on 2007-01-24
Run the command again but this time, put a **sudo** in front of it.

---

