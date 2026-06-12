---
title: "broken package -- cannot install Skype"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by scubacuda on 2006-03-12
**Solved**: [Here's what I did](https://wiki.ubuntu.com/Skype?highlight=%28skype%29)

**********************************************
**********************************************

Shortly after running **sudo apt-get dist-upgrade**, I [tried to install Skype](http://www.skype.com/download/skype/linux/repositories.html) and got this error.

```
$ sudo apt-get install skype

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
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Broken packages

```

---

