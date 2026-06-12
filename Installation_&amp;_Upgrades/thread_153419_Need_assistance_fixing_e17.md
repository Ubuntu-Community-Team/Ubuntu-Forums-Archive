---
title: "Need assistance fixing e17"
date: 2006-03-31
forum: Installation &amp; Upgrades
---

### Post by hampton275 on 2006-03-31
I installed e17 from CVS, there is a thread on the forums I used. After relizing I was having a few problems. eutils wouldn't install, etc I figured I would uninstall my e16 install to install e.16.999. However I am getting a tonne of dependencies. They seem to be related to libcurl3, but I am a little out of my element. If anyone knows how to clean out a CV install of E17 and install the e .16.999, so I meet the dependencies, that would be great.
TIA

~$ sudo apt-get install enlightenment
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
  enlightenment: Depends: libcurl3 (>= 7.15.0-1) but 7.14.0-2ubuntu1.2 is to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
                 Depends: libevas0 but it is not going to be installed
                 Depends: libidn11 (>= 0.5.18) but 0.5.13-1.0 is to be installed
                 Depends: libkrb53 (>= 1.4.2) but 1.3.6-4 is to be installed
                 Depends: libssl0.9.8 (>= 0.9.8a-1) but it is not installable
                 Depends: libe but it is not going to be installed
                 Depends: libevas
                 Depends: libecore
                 Depends: libedje
E: Broken packages

---

