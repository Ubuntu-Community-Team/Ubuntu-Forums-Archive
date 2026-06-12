---
title: "Gutsy upgrade went hideously wrong - Or atleast I thought it did"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by speedsix on 2007-10-18
Rather impatiently did an upgrade from Festy to Gutsy last night using the recommended update-manager method. All was going well until it started throwing up some errors for seemingly all the important packages (sudo, login etc.) It kept saying could not install the package because of dependancy problems. Alot of the packages went through ok but like I say alot of the important ones threw up this error.

Anyway, I left the machine for a while, came back and update manager had dissapeare but it hadn't rebooted by the look of it (my terminal was still open) Rebooted and surprisngly all is well. Check synaptic for updates, none available. All the packages that errored list (Gutsy) as the version.

Anyone got any idea why I got all those dependancy errors but the packages all seem to be upgraded ok? Also is there anything I can run to make sure I have all the correct packages and everything is ok?

I'd like to avoid a reformat if there's no point.



Thanks

---

### Post by agent8131 on 2007-10-18
I would try this:

sudo apt-get install apt-show-versions

apt-show-versions | grep -v gutsy

That will show you all installed packages not a part of gutsy.  If you see a few that's probably fine.  If you see a lot that probably indicates a problem.

---

