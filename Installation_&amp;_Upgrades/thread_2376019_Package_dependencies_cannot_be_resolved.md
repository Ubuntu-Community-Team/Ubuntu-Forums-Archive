---
title: "Package dependencies cannot be resolved"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by mekromancer on 2017-10-29
Hi all, please bare with me because I am new to Ubuntu (on 16.04 LTS) but I'm not sure where else to turn to for help. As I try to go through the Software Updater like I routinely do without problem, an error message now pops up every time now and new updates no longer show up on a blank list.

The error message pop-up says:
**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

and on the top right corner of the menu bar is a red warning icon with the following message when clicking on it:

'Error: Marking the upgrade (E:Error,pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.)''
This usually means that your installed packages have unmet dependencies

What can I do to resolve this error and continue receiving new updates?

---

### Post by ian-weisser on 2017-10-29
The most common common cause of this particular error message is that you unwisely installed software from a PPA or other non-Ubuntu source.
If that's what you did, then uninstall the software and delete the source.
If you are *really sure* you didn't do that, then search your memory carefully and tell us exactly what you installed *before* you encountered the problem.

---

### Post by Impavidus on 2017-10-30
In addition to the above, could you run
```

sudo apt update
sudo apt upgrade

```
in a terminal (you won't get any visual feedback when you type the password) and paste the output here? Use code tags, like I did just above. That should give us some error messages telling what's going wrong.

---

