---
title: "multiple version of same package. How to clean ?"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by cremersdh on 2010-05-10
I have (after upgrading from 9.10 to 10.04) several packages who are installed with multiple versions. 

e.g. Python
[SIZE="1"]
dpkg -l | grep python2
ii  libpython2.6                         2.6.5-1ubuntu6                                         Shared Python runtime library (version 2.6)
rc  python2.4                            2.4.6-1ubuntu3.2.9.10.1                                An interactive high-level object-oriented la
rc  python2.4-minimal                    2.4.6-1ubuntu3.2.9.10.1                                A minimal subset of the Python language (ver
rc  python2.5                            2.5.4-1ubuntu6.1                                       An interactive high-level object-oriented la
rc  python2.5-minimal                    2.5.4-1ubuntu6.1                                       A minimal subset of the Python language (ver
ii  python2.6                            2.6.5-1ubuntu6                                         An interactive high-level object-oriented la
ii  python2.6-minimal                    2.6.5-1ubuntu6                                         A minimal subset of the Python language (ver[/SIZE]


I guess I only need the newest one .. The other ones have status "RC"
Or am I wrong here, and do I need to keep these old versions ?????

So how do I get rid off 2.4 and 2.5 and just keep version 2.6. How can I easily remove these "old" packages. I tried aptitude purge, aptitude clean, aptitude autoclean. But they don't do the trick.

I am looking for an easy way, because python is only an example. Else I could just delete them be using their name.... (of course)

Why did these stay on my system anyway ?

---

### Post by narendraD on 2010-05-10
When you open Synaptic, you will see on the left side a selection that says Installed (Residual Config) or Auto Uninstall. Select all packages so marked and uninstall Completely.

---

