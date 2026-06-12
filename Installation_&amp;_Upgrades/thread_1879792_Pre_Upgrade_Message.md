---
title: "Pre Upgrade Message"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2011-11-12
I started the upgrade and then got this message. Is this going to create problems. Am I opening the proverbial can of worms.


Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

---

### Post by ElGaton on 2011-11-12
No, that message simply tells you that some custom PPAs you have added will be disabled on the new installation, that's simply because some of their owners forget or do not want to release updated packages for the new Ubuntu versions.

There's no harm in proceeding, just remind that the software packages you have installed from PPAs might not get any updates in the future.

If you want to check whether PPAs have updated packages for the new Ubuntu version, just open Software Sources and click on the "Other Software" tab. From the list of PPAs you have added, select the one(s) you wish to activate again and click on "Edit", then change the "Distribution" field to the name of the Ubuntu version you have upgraded to, in lowercase (for example, "oneiric"). Confirm with "OK" and mark the checkbox next to the PPA in the list, then click on Close and, when asked to update the package lists, do so. If an error shows up, then at least one PPA does not provide updated packages; for this reason, I recommend you to re-enable one PPA at a time and check.

---

