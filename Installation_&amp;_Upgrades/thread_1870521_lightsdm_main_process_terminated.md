---
title: "lightsdm main process terminated"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by jeff17237 on 2011-10-27
I just upgraded to 11.10, and as with every upgrade it never boots afterward.  However, this one I have not been able to solve.  Errors:

1)  init: lightsdm main process (3658) terminated with status 1
2)  iwlagn 000:04:00,0: Microcode SW error detected.  Restarting 0x2000000.

I am assuming that the second error (wireless card problem) has nothing to do with the failed boot.

I already tried reconfiguring graphics and reinstalling AMD driver.  I have not yet tried to boot recovery/liveCD.  I will try that in an hour or so when I have time and post back an update.

The first time I booted, after a disk check it said "cannot find /tmp" or something to that effect.  I let it try to fix itself but it never did.  Every boot since has not given that error.  Unrelated?

Thanks for the help.

EDIT:  Boot to recovery doesnt change anything, but add a new error "init: ureadahead main process (341) terminated"

EDIT2: More gibberish from attempted boots:
1) /etc/rc2.d/S99acpi-support: line 7: /usr/share/acpi-support/power-funcs: No such file or directory
2) init: plymouth-upstart-bridge main process (3639) killed by TERM signal

Google/wandering the forums is not yielding anything.  It boots to prompt after 11.10 tries to load so I have been trying to wander a little bit with no luck.

---

