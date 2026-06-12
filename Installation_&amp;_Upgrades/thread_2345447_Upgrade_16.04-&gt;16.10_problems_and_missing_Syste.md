---
title: "Upgrade 16.04-&gt;16.10 problems and missing System Settings icons"
date: 2016-12-04
forum: Installation &amp; Upgrades
---

### Post by maxdom on 2016-12-04
I've upgraded 2 different desktop machines in the past couple of days, and I'm seeing the same problems on both.
I initiated the upgrade like this:
[B]sudo apt update && sudo apt upgrade
sudo apt do-release-upgrade

[/B][FONT=arial]After a while the upgrade process hangs on this last message:
Processing triggers for libc-bin
Pressing enter gives me back the shell prompt (although not working properly).
At this point, running sudo apt update will tell me there's 1000-and-odd number of packages needing an update.

Running sudo apt dist-upgrade will finish the upgrade process it seems.

Things seems fine after this, BUT the system settings screen (unity-control-center) now only has 1 or 2 icons in it, depending on running it from the Launcher or from command line.
Those icons are: Language Support and Software & Updates. (The latter only in the command line case)

I've searched for and found some references to missing system settings icons, but those were mainly old ones, and did not apply to me, I believe.

Any suggestions are appreciated.
Thanks.

BR,
Rolf[/FONT]

---

