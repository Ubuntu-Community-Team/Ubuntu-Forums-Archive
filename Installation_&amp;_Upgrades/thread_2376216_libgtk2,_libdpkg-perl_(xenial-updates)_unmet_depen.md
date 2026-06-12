---
title: "libgtk2, libdpkg-perl (xenial-updates): unmet dependencies"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by rooker2 on 2017-10-31
On a fresh install of Xubuntu 16.04.3 (xenial), I'm experiencing strange "unmet dependencies" on rather common packages.

Some packages require a very specific version that is superseeded in e.g. proposed-updates repositories.
Therefore some programs can't be installed, unless certain libraries are downgraded and forced to an older version.


**Example 1: "libdpkg-perl":**
The problem is that "libdpkg-perl" won't install because a minor-updated version is available, but a specific version (=main repository) is required:
> dpkg-dev : Depends: libdpkg-perl (= 1.18.4ubuntu1) but 1.18.4ubuntu1.2 is to be installed
            Recommends: build-essential but it is not going to be installed
            Recommends: libalgorithm-merge-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

[B]Example 2: "libgtk2.0-0":
[/B]The problem is that "libgtk2.0-0" won't install because a minor-updated  version is available, but a specific version (=main repository) is  required:> libgail18 : Depends: libgtk2.0-0 (= 2.24.30-1ubuntu1) but 2.24.30-1ubuntu1.16.04.1 is to be installed

What puzzles me is that I know issues like this when mixing default repositories, but I've had these problems before adding any non-standard apt-sources.
Any ideas?
Anyone else experiencing this?


Thanks in advance :)

---

### Post by ajgreeny on 2017-10-31
Strange because I already have 2.24.30-1ubuntu1.16.04.2 so I am uncertain what is going on.

What are you trying to install that requires the proposed repos; those repos can often lead to problems of this sort.

---

### Post by mc4man on 2017-10-31
Make sure you have xenial-updates & xenial-security enabled in your sources. Everything you mentioned that I checked is in those repos, not -proposed.

---

