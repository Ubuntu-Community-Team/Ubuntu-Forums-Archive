---
title: "Help upgrading libcairo2"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by tahnok on 2006-12-24
Whenever update manager notifies me of new updates, I get this message saying that it cannot install libcairo2 and that I should run apt-get dist-upgrade, I tried it and the output is ```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libcairo2 libcairo2-dev
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```
So I tried installing the packages manually but I get this error when running sudo apt-get install libcairo2
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libcairo2: Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
E: Broken packages
```

Please help me fix this

EDIT: I just did a search for libcairo2 and someone else had this problem.It's apparently not something fatal, and there is nothing that can be fixed at the moment. I should have searched more thoroughly before posting,

---

### Post by soul814 on 2007-02-26
I was wondering if you ever got this fixed because I am having the same problem.

---

