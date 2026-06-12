---
title: "Upgrade from 10.10 to 11.04 fails"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by NSim on 2011-09-29
Hello,

I am trying to upgrade from 10.10 to 11.04 but the update manager fails at so many levels. Any suggestions? This is the output:
```
The following packages have unmet dependencies:
 dbus : Depends: upstart-job
        Depends: upstart (>= 0.6.3-6) but it is not going to be installed
 hostname : PreDepends: upstart-job
 logrotate : Depends: cron or
                      anacron but it is not going to be installed or
                      fcron but it is not going to be installed
 module-init-tools : Depends: upstart-job
 netbase : Depends: initscripts but it is not going to be installed
           Depends: upstart-job
           Recommends: ifupdown
 procps : Depends: upstart-job
          Depends: initscripts but it is not going to be installed
 udev : Depends: upstart-job
 util-linux : Depends: upstart-job
 x11-common : Depends: upstart-job
 xserver-xorg-core : Depends: keyboard-configuration but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

I manually reinstalled all the packages but there are no changes

Thanks,
Nikola

---

### Post by zvacet on 2011-09-30
In terminal

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by NSim on 2011-10-07
Unfortunately I did this, and its not working. I think something is wrong with one or several PPA packages. If I use PPA-purge I dont know which of these packets to purge.

Any other suggestions,

Thanks

---

### Post by dino99 on 2011-10-07
of course ppa(s) is/are to blame, purge them all first

on my side, i've made this upgrade yesterday, and dont got issue at all.

---

