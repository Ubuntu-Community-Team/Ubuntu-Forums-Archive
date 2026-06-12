---
title: "Arduino is already the newest version (2:1.0.5+dfsg2-4) so that no"
date: 2016-11-07
forum: Installation &amp; Upgrades
---

### Post by maxsteffens on 2016-11-07
Why repository still have the old version of the Arduino IDE?
And when she is going to be updated?
ARDUINO 1.6.12                         is the new.
:(

---

### Post by deadflowr on 2016-11-07
The repositories are locked to whatever the package version was at when the development of Ubuntu was frozen.
If a particular package wasn't packaged in time for adequate testing, then it wasn't included post final freeze.
And it won't get added to the repos post release.

Packages can also get held back if during testing a problem arose that could not be resolved before release.
Those packages also will not ever make it into the repos for that release.

---

### Post by maxsteffens on 2016-11-08
Prediction to include new packages?
Repository is frozen at the moment?

---

### Post by deadflowr on 2016-11-08
> **maxsteffens said:**
> Prediction to include new packages?
Repository is frozen at the moment?

?
Depending on whether or not a maintainer for a package gets it built in time for testing during the Ubuntu development cycle (currently for 17.04/zesty zapus)
before the set freeze time.

The repos aren't frozen.
The packages are frozen at whatever version they were at the developments freeze time.
Packages can and do get updates, which are typically small patches.
They prefer updates using small patches so as to minimize any disruption.

(Newer versions might need a user to do a complete overhaul of the settings they use, or might include or exclude a feature they commonly use. These instances can cause far reaching disruptions.
Patches allow existing systems to run as they have (as they do not reset settings anew, nor remove or add any function), barring the patch causes regressive behavior.

(from time to time a patch does cause a regression, and so the maintainers have to run a new update that removes or disables or fixes the patch.)


Of course then there are exceptions to all of this.
Firefox is a great example, as when Firefox gets an update, it's a whole package update to the newest stable version.
But Firefox and browsers as a whole usually contain so many security related fixes that it's very difficult and not worthwhile to simply add a lot of patches every time it needs to be patched.
In these cases, it's just easier to upgrade the package version.
But that's just how I see it.

---

