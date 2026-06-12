---
title: "Upgrade From 7.04 to 7.10 Failed - Scared To Reboot!"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by umechanism on 2007-12-28
I am running Kubuntu 7.04 and I used Adept to try to upgrade from 7.04 to 7.10.  Soon after the installation begin, I received a message that some third party sources were deactivated in my sources list but I could enable them again after the installation.  Okay.  No problem. 

The installation seemed to be going smoothly enough but after about the third step of the installation I received the following error message:

"**Could not install "debconf" - the upgrade will continue but the "deb conf" package may not be in a working state.  Please consider submitting a bug report about it.  [subprocess post-installation script killed by signal (segmentation fault), core dumped**."

A few seconds later - another error message along the same lines:

"Co**uld not install /var/cache/apt/archives/x11-common_1%3a7.2-5ubuntu13-i386.deb**."

A few more messages like that one appeared.  Then, the whole download seem to freeze at 2%.  It said it was "preparing liborbit2-dev" and that there were 5 hrs and 51 minutes remaining.  After 1 hour, it was still at 2% completion with the same status.

So, fearing the worst, I canceled the upgrade.  Now I am afraid to reboot my machine.  I know Adept downloaded about 700 megs of files but I do not believe they were installed.

What should I do?

M

---

### Post by Pumalite on 2007-12-28
Save /home and data and do a clean install.

---

### Post by incarnis on 2007-12-30
That's a bit extreme. The answer isn't always to do a clean install.

If this happens:

1. Abort the Adept manager
2. ps -ef | grep adept | grep -i adept  and kill all the processes you see
3. Open a console, su to root
4. Do apt-get install debconf. You will see loads of errors.
5. Do apt-get -f install as it suggests

This should do a load of installs and fix debconf etc.

You can then restart adept manager, hit "fetch updates" then "Version upgrade".

No need for a reboot, eh?

Simon

---

