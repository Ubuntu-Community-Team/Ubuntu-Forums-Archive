---
title: "Blocked installing Rosegarden"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by ongaku on 2007-05-12
I am a long time user of Linux and decided to move from RHEL3 to Ubuntu as I no longer need RHEL3 for work.

I've heard good things about Ubuntu, so.....

One thing I would like to do is bring up Rosegarden, but I've run into a problem.

I downloaded the 'deb' file and tried to install.  I got this complaint:

         problem: dependency is not satisfiable: liblo0
Okay.....I downloaded and successfully installed liblo0.
But the install of Rosegarden still says the dependency is not met

I ran kpackage to verify that liblo0 is there, and it is.

So what gives?  Any ideas?

Also, on a more general level....wouldn't we all be better off of everybody just linked statically?  I suppose that is a different thread.

Also, when I installed (from Linux Format CD) I was surprised that I didn't get asked what packages I wanted...is this normal?

Thanks....
John

---

### Post by rondackcpu on 2007-05-13
Welcome, John,

I have no experience with Red Hat so I don't know how package installation goes there, but I would try the Synaptic Package Manager first in Ubuntu rather than just try to install a Deb binary.  The Synaptic Manager usually resolves all dependency issues automatically. 

Try System >> Synaptic >> scroll down to "Rosegarden" >> click the box  >> click mark for install (the list of dependencies will pop up) >> click to continue >> click "Apply".

"Should be duck soup."

CRS

---

