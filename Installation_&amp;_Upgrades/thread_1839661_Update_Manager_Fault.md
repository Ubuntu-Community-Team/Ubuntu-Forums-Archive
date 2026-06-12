---
title: "Update Manager Fault"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by munkee on 2011-09-06
When I have been attempting to check for new updates over the last 24 hours with the Update Manager, it has been falling over with the error message below:

 "Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug in the 'update-manager' package and try to include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'"

The Update Manager reports there are 3 updates, however when I check Synaptic I can only find one (libv4l.so).

I have run apt-get update, upgrade, clean, and autoclean commands; but the problem still persists.

Has any one else come across this, and is there a workaround or fix for this issue?

---

### Post by raja.genupula on 2011-09-06
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/154715](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/154715)


Hey man do this , i think it can help you to solve your issue . 
let us know what you got .

---

### Post by munkee on 2011-09-06
Thanks Raja.  It looks like I had a broken PPA.  I have now unchecked most of the PPAs I have set up in Software Sources, and I'm now able to run the update manager.  I'm going to recheck them one by one to see which PPA is causing the problem.

All the best.

---

### Post by raja.genupula on 2011-09-07
hope that link helps you to solve your issue

---

