---
title: "Upgrade failed"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2010-10-16
[I][B]"Could not install the upgrades
Error during commit
'E:Couldn't configure pre-depend openoffice.org-common for openoffice.org-report-builder, probably a dependency cycle.'
Restoring original system state"[/B][/I]

Is this normal...and what do I do about it?

---

### Post by dino99 on 2010-10-16
remove/purge then reinstall the package(s) with synaptic

---

### Post by arvevans on 2010-10-16
Used Synaptic to "Totally Remove" Open Office...and still get this when 
trying to upgrade from 10.4 to 10.10:

[INDENT]Could not install the upgrades

Error during commit
'E:Couldn't configure pre-depend openoffice.org-common for openoffice.org-report-builder, probably a dependency cycle.'
Restoring original system state[/INDENT]

What next?

---

### Post by arvevans on 2010-10-16
Please wait for a few minutes.  I just found that OO Report-builder is not part of Open Office.  I have now "totally Removed" the report builder as well and will try again with the upgrade.

---

### Post by arvevans on 2010-10-16
Okay...removing OO-Report Generator fixed the problem.
Changing this threads status to SOLVED.

Thanks for the push in the right direction.

---

