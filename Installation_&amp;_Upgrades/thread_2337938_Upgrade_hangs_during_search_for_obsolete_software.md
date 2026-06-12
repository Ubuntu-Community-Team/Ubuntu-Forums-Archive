---
title: "Upgrade hangs during search for obsolete software"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by swajime on 2016-09-22
My computer asked me if I wanted to upgrade to 16.04, and I clicked yes.
The upgrade stalled in the "Cleaning up" step.
It says "Searching for obsolete software" and the terminal text displays this:

     ...
     173 new root certificates were added to your trust store.
     Import process completed.
     Done
     done.

The window greys out for a few seconds, then becomes active again for a few seconds, over and over again.

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"

$ uname -a
Linux desktop 3.13.0-96-generic #143-Ubuntu SMP Mon Aug 29 20:15:20 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

What should I do to finish the upgrade?

---

### Post by swajime on 2016-09-24
Update:

An untimely power failure occurred whilst waiting for an answer.  :-(
Fortunately, the system started up ok.

The only problem I noticed so far was that Eclipse quit running.  It could no longer find JDK 7, as it was replaced with JDK 8 during the upgrade.  I reran the install script for Eclipse and now it is running ok.

I'm still curious to know if there is anything else that should be done.

Thanks,


John

---

### Post by swajime on 2016-09-24
Hmmm....

So, I've rerun the Eclipse install script, reinstalled EPIC, and reinstalled libpadwalker-perl.  But the debugger in Eclipse for Perl is no longer working.  Pressing the debug icon has no effect.  It does not even switch to the Debugger perspective.

Ack :-(

---

### Post by swajime on 2016-09-25
Removed cpp-mars directory altogether and reinstalled.  Debug works now.  :-)

---

