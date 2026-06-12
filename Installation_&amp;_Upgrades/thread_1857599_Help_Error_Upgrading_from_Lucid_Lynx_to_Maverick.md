---
title: "Help: Error Upgrading from Lucid Lynx to Maverick"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by bluec10 on 2011-10-10
I'm running Ubuntu 10.04 Lucid Lynx and I want to progressively upgrade to the latest version. As I move from 10.04 to 10.10 I receive this message:

[INDENT]Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.[/INDENT]

I've uninstalled all non-Ubuntu software and used the clean-up tool. I have not installed any beta releases, but have simply tried to keep up with regular releases sent by Ubuntu.

Any suggestions for me?

---

### Post by Claus7 on 2011-10-10
Hello,

I had the same problem, while trying to update previous versions of ubuntu. That means, that some packages cannot be upgraded because their dependencies stopped somehow being upgraded. 

You have to solve unmet dependencies first and then try to upgrade. It is a long story, because this has not to do necessarily with non - ubuntu packages, and if you try to remove some, your system might become unstable and then difficult to upgrade.

If fresh installation is not an option, I would be curious to see how you tackled the problem. I'm not on that old pc right now, where I had kept some notes about the commands I had executed.

Good luck,
Regards!

---

