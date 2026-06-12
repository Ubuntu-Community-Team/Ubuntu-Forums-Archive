---
title: "Could not calculate the upgrade (to 12.04)"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by johnzbesko on 2012-05-29
Attempted to upgrade from 11.10 to 12.04. Got the error:

Could not calculate the upgrade.
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Searching for a solution, I was instructed to install rkward. I think I installed the latest KDE (I now have the 12.04 splash screen.) However, I still can't install 12.04. I guess my original problem may have been a weird dependency problem with melt/mlt when trying to install openshot (conflicted with kdenlive.)

I've tried to uninstall anything involved with mlt. No luck. How can I uninstall all versions on KDE, current and legacy? Then, maybe, the upgrade will work. Any other way of diagnosing the upgrade problem?

I really don't want to do a fresh install...

Thank you for your help.

"Whoever you are, I have always depended on the kindness of strangers." Blanche DuBois, A Streetcar Named Desire

---

### Post by johnzbesko on 2012-06-09
SOLVED: I found a bunch of HELD packages when I examined the proper log file. When I removed the last one listed (something I did not recognize) I was suddenly able to complete the upgrade.

---

