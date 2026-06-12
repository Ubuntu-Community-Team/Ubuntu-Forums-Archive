---
title: "Switched off during upgrade, now what?"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by JDailey on 2011-05-02
I was upgrading from 10.10 to 11.04 and an office mate thought the computer was unresponsive.  So, he turned it off and back on.  Now the screen says: > inti: udevtrigger main process (96) terminated with status 1
init: udevtrigger post-stop process (99) terminated with status 1
init: udevmonitor main process (95) killed by TERM signal 
mountall: Disconnected from Plymouth
init: plymouth main process(54) killed by SEGV signal
init: plymouth-splash main process (100) terminated with status 2
So, I am guessing a new install from a CD/USB is in order but maybe not.  So if there any suggestions to how to recover this I would appreciate it.  I have 4 hours till the iso download finishes and then another hour or so until I will be able to finish and start an install.  No biggie, I will spend the time with a blow torch and a pair of pliers.

---

### Post by JDailey on 2011-05-02
Messed around with the Grub menu to see if I could get it to twitch and to no avail.  I looks like the root is missing.  going to reinstall Maverick so that people can start working soon.

---

### Post by wilee-nilee on 2011-05-02
> **JDailey said:**
> Messed around with the Grub menu to see if I could get it to twitch and to no avail.  I looks like the root is missing.  going to reinstall Maverick so that people can start working soon.

I would try 
sudo apt-get -f install
from a command line by booting recovery stanza in the grub menu. Probably to late here but the command may unlock the upgrade and finish it.

---

