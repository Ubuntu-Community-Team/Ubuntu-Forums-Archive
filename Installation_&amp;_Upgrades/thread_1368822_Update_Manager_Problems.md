---
title: "Update Manager Problems"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by nishant.singh28 on 2009-12-31
When I try to Update or press Reload in Synaptic Package manager, I get the following error:
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
 What's the problem? I updated on 28th and it worked fine. And now!!!

---

### Post by shredder12 on 2009-12-31
this error arise when you are trying to install or update using apt or aptitude and there is already a similar application(say synaptic) open which has already locked the resources.
probably restarting will solve the issue.

---

### Post by MelDJ on 2009-12-31
or try sudo pkill apt to kill apt

---

