---
title: "realplayer needs xlibs (not installable)"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2006-07-19
Can someone explain the following and how to get around this?

```
root@mico1:/home/mico# apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  realplayer: Depends: xlibs but it is not installable
E: Broken packages

```

---

### Post by Titus A Duxass on 2006-07-19
Can't explain it, but a work around is to use Automatix and install realplayer through that. It's the easiest way.

---

