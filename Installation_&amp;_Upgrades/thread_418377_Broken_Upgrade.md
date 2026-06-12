---
title: "Broken Upgrade"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by SoggyCornflake on 2007-04-22
I launched the upgrade from edgy to fiesty and went to bed.

When I got up this morning, I found the install broken. Update manager suggested that I run apt-get -f install and this is the result.```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  gnucash: Depends: libgnome-keyring0 (>= 0.7.1) but 0.6.0-0ubuntu2 is installed
           Depends: libgnomeprint2.2-0 (>= 2.17.0) but 2.12.1-5ubuntu1 is installed
           Depends: libgnomeprintui2.2-0 (>= 2.17.0) but 2.12.1-4ubuntu2 is installed
           Depends: libgnomeui-0 (>= 2.17.1) but 2.16.1-0ubuntu2 is installed
           Depends: libgnomevfs2-0 (>= 2.17.90) but 2.16.1-0ubuntu7 is installed
           Depends: libgsf-1-114 (>= 1.14.3) but 1.14.1-2ubuntu1.1 is installed
           Depends: libgsf-gnome-1-114 (>= 1.14.3) but 1.14.1-2ubuntu1.1 is installed
           Depends: libgtkhtml3.8-15 (>= 3.13.6) but 3.12.1-0ubuntu1 is installed
           Depends: libofx3 but it is not installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libstdc++6-4.1-dev: Depends: libstdc++6 (>= 4.1.2-0ubuntu4) but 4.1.1-13ubuntu5 is installed
  python-examples: Depends: python (= 2.5.1~rc1-0ubuntu3) but 2.4.3-11ubuntu3 is installed
  python2.4-gd: Depends: libgd2-noxpm (>= 2.0.33) but it is not installed or
                         libgd2-xpm (>= 2.0.33) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
I tried to remove gnucash, but that doesn't work.

Does anybody have an easy suggestion to get me through this?

Thanks in advance

---

### Post by SoggyCornflake on 2007-04-22
I figured it out:

I used ```
sudo dpkg -r gnucash
```

That fixed the problem

---

