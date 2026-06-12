---
title: "Unable to install gcc-4.9-base:i386 package"
date: 2015-10-15
forum: Installation &amp; Upgrades
---

### Post by Salissar on 2015-10-15
I've been running into some problems while trying to install wine and steam on Ubuntu 14.04, and they all seem to stem from the gcc-4.9-base:i386 package.


When I run *sudo apt-get install gcc-4.9-base:i386*, I get this:

```
Some packages could not be installed. 
This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. 
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libdee-1.0-4 : Depends: libicu52 (>= 52~m1-1~) but it is not going to be installed
libgcc1 : Depends: gcc-4.9-base (= 4.9.2-0ubuntu1~12.04) but it is not going to be installed
liblapack3 : Depends: libgfortran3 (>= 4.6) but it is not going to be installed
libstdc++6 : Depends: gcc-4.9-base (= 4.9.2-0ubuntu1~12.04) but it is not going to be 
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

However, when I try to run* sudo apt-get install gcc-4.9* (or any of the other dependencies above), I get that the package's already installed:

```
gcc-4.9-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

It also doesn't seem to be an issue of holding broken packages, as running *dpkg --get-selections | grep hold* returns nothing.


I've added the i386 architecture to dpkg and tried the different solutions found online (most of which seem to be *sudo apt-get update && sudo apt-get upgrade*), but nothing seems to work so far.

---

### Post by ian-weisser on 2015-10-16
> **Salissar said:**
> libdee-1.0-4 : Depends: libicu52 (>= **52~m1-1~**) but it is not going to be installed

52~m1-1~ is not a valid version number of libicu52 in the Ubuntu repositories.
It seems likely that you have added a different source, and that non-Ubuntu source has introduced a version conflict.

Determine the offending source using the 'apt-cache policy' command.
Remove that source from your sources list.
Uninstall all software that came from that source.
Delete all packages from that source from your cache.
Refresh your package database without the offending source.
Reinstall the deleted software from the Ubuntu repositories.

---

