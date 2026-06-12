---
title: "Problem with &quot;make install&quot; Intel WiFi driver"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by PositronLaser on 2007-06-15
When I try installing intel wifi driver and type "make install," I get this error message:
> root@Flanker:~/Desktop/iwlwifi-0.0.30# make install
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'.  Stop.
When I do what it suggests (typing 'make=SHELL=/bin/bash'), I get this error message:
> Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source'
make: *** [compatible/kversion] Error 1

Could somebody explain to me what this means and what I should do to fix it?
Thanks,

---

### Post by JoePits on 2007-06-15
sorry bud i can't help you.  ive been trying for a  few days now to get some help for that problem on this forum

tried irc.freenode.net #ipw2100 which is the official channel for iwlwifi got no help just a bunch of people trying to sound smarter than me.

theres a bug report about it here:
[http://bughost.org/bugzilla/show_bug.cgi?id=1301](http://bughost.org/bugzilla/show_bug.cgi?id=1301)

its something to do with feisty and the kernel sources.  though the packages are installed, maybe they are bugged themselves?

---

### Post by JoePits on 2007-06-15
im updating to gutsy tonight going to see if that helps.

---

### Post by PositronLaser on 2007-06-15
Bump, anybody?

---

