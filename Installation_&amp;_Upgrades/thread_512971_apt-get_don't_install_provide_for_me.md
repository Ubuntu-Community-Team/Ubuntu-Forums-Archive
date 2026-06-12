---
title: "apt-get don't install provide for me"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by gogoliu on 2007-07-29
I create apt.conf and some necessary directorys, add debian-installer source to sources.list. When I _apt-get install libdebian-installer4-udeb_, apt-get wouldn't install libc6-udeb for me. It report:
[INDENT]Reading package lists... Done
Building dependency tree... Done
Note, selecting libc6-udeb instead of libc6
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdebian-installer4-udeb: Depends: libc6 (>= 2.5-0ubuntu1)
E: Broken packages[/INDENT]

I use apt-get install libc6-udeb libdebian-installer4-udeb, the result is same.
How to make apt-get install libc6-udeb for me?

---

