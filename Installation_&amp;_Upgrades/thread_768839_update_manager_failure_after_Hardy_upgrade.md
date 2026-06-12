---
title: "update manager failure after Hardy upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by luckydog on 2008-04-26
I did an upgrade to Hardy using Synaptic. It disabled some of my sources & said that I could re-enable them after the upgrade. Now, when I try to enable them again, Synaptic crashes with the following error:

Could not initiate the package information

A unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 65 in source list /etc/apt/sources.list(dist parse),E:The list of sources could not be read.'

I can usually muck my way through problems using the forums, but this one has proved to be a tough one to solve. Any help will be appreciated.

---

### Post by luckydog on 2008-04-26
Never mind, I commented out the offending line in etc/apt/sources.list, & now I'm back to loving Ubuntu once again.

---

