---
title: "Gutsy upgrade failed but thinks it worked"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by im7766 on 2007-11-06
Upgraded from Feisty after getting it up-to-date.
Downloaded files OK.
During installation got a few error messages about packages that could not be installed, "The upgrade will continue but the ... package may be in a not working state. Please consider submitting a bugreport about it."
Then near the end it all froze.
Could not get anything to respond. tried ctrl-alt-backspace
So now I have a system that grub offers me Gutsy but it won't boot, appears totally dead. The other offerings e.g. recovery mode or generic recovery mode won't boot either.
Feisty still works a bit.

I have no idea how/if it's possible to remove the "upgrade" or force it to do the upgrade again.

Very confused at this point.

---

### Post by im7766 on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/115616](https://bugs.launchpad.net/bugs/115616) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				No help about how to roll back or uninstall Gutsy after a horrible upgrade?

Well the Gutsy installation wasn't *totally* unusable, but loads pf problems, as I now discuss:

Using the generic recovery boot option, I got as far as a failure with entries like
"device-manager" "dm-linear" "Device lookup failed"
Hundreds of them, one after the other.
I found a bug on [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
 - [https://bugs.launchpad.net/bugs/115616](https://bugs.launchpad.net/bugs/115616)

that led to changing  /etc/evms.conf: in sysfs_devices:
include = [ ]
exclude = [ * ]

This seemed to get the booting further, and even the other 3 Gutsy boot options (normal, recovery, generic) seemed to get a bit further.
They then seem to report some problem about fan or CPU speed and non-existent missing file/folders. Will have to try to capture the details exactly and pursue that too.

So far feeling pretty fed up with the upgrade experince :-(

---

