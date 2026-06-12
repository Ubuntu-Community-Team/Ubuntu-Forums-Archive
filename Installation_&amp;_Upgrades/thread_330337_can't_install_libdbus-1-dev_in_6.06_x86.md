---
title: "can't install libdbus-1-dev in 6.06 x86"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by sles on 2007-01-03
Hello!

Yesterday I installed this lib at work on amd64.
But I can't do it at home on x86:

 apt-get install libdbus-1-dev
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
  libdbus-1-dev: Depends: libdbus-1-2 (= 0.60-6ubuntu8) but 0.62-bmp1ubuntu1 is to be installed
E: Broken packages


As I see lib has greater version then headers.
How can I fix this?

---

