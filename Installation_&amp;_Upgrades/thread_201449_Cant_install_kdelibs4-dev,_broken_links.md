---
title: "Cant install kdelibs4-dev, broken links"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by w1z4rd on 2006-06-21
Im trying to install, kdelibs4-dev, but not matter how many sources list I try, I keep getting the following errors:

> w1z4rd@b0x:~/src$ sudo apt-get install kdelibs4-dev
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
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.2-0ubuntu18) but 4:3.5.3-0ubuntu0.1 is to be installed
                Depends: kdelibs-bin (= 4:3.5.2-0ubuntu18) but 4:3.5.3-0ubuntu0.1 is to be installed
                Depends: libarts1-dev (>= 1.5-rc1) but it is not going to be installed
                Depends: libqt3-mt-dev (>= 3:3.3.5) but it is not going to be installed
                Depends: libavahi-qt3-dev but it is not going to be installed
E: Broken packages
w1z4rd@b0x:~/src$     

Any suggestions?

---

