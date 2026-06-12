---
title: "Need help installing Gaim: Error given"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by ant80 on 2006-08-06
When I install gaim using the following command: 
```
sudo apt-get install gaim
```

> Reading package lists... Done
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
  gaim: Depends: gaim-data (= 1:1.1.4-1ubuntu4.4) but 1:1.4.0-1ubuntu1~5.04ubp1 is to be installed
E: Broken packages


Please help because I don't know what to do. Thanks.

---

### Post by costoa on 2006-08-06
Just curious, why not just use Synaptic Package Manager (gksu /usr/sbin/synaptic) to install Gaim? Since Gaim is installed with ubuntu-desktop I should ask were there any initial installation problems?

---

