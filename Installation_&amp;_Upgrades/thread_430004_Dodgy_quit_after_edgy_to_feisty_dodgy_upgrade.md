---
title: "Dodgy quit after edgy to feisty dodgy upgrade"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by mjshepherd on 2007-05-01
Can anyone help me with an annoying niggly problem?  I recently upgraded from edgy to feisty using upgrade manager, and unfortunately, after running the thing for about 12 hours, the computer got turned off after freezing towards the end of the upgrade process.  Ubuntu boots OK, and everything seemed to work.

Everything, that is, except the "quit" option under the System menu - clicking on this sends me back to the log-in screen for a second or two, then my screen goes completely bananas, showing a smaller version of my desktop background, loads of repeated lines and a chunk of some random internet pop-up (last time it was something to do with e-bay!).  Then i have to switch the power off.

Following the aborted upgrade the update manager told me to run a partial upgrade.  I did this and only a 10 files needed downloading and installing.  I did the partial upgrade, and got some error messages: "could not install 'hal', 'gnome power manager' and 'hwdb-client-common' because they were already installed and configured. "So what?" I thought.  Then i got:
error: root: SystemError from cache commit(): E Sub-process /usr/bin/dpkg returned an error code (1)
update manager:Fatal IO error 9 (Bad file descriptor) on X server 0.0.
and the whole thing gave up.  It suggested I log a bug report with launchpad.  I tried but launchpad crashed.

Any ideas how to fix my upgrade, and allow me to stand by, change users, log out and shut down the normal way?

---

### Post by mjshepherd on 2007-05-01
After a complete crash running f-spot, i rebooted and did a sudo apt-get upgrade (nothing changed, apparently) then a sudo apt-get update, which loaded a load of stuff, and now everything works just fine.  I've no idea what i've done, though...

---

