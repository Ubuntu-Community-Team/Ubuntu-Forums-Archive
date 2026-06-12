---
title: "install blocked update, not karmic"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by sripplinger on 2009-12-12
I have some blocked updates available.  I don't want to install karmic, though.  If I run sudo apt-get dist-upgrade will it install karmic?  If so, is there a way to install the blocked updates without installing karmic?

---

### Post by slakkie on 2009-12-12
Could you post the output of aptitude -s safe-upgrade (and perhaps aptitude -s full-upgrade) so we know what is actually going on. Many thanks!

ps. put the output in/between [ code] [ /code] tags (without the spaces).

---

### Post by sripplinger on 2009-12-12
Sure...

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  libdns46{a} linux-backports-modules-2.6.28-17-generic{a} linux-headers-2.6.28-17{a}
  linux-headers-2.6.28-17-generic{a} linux-image-2.6.28-17-generic{a}
  linux-restricted-modules-2.6.28-17-generic{a}
The following packages will be REMOVED:
  linux-backports-modules-2.6.28-15-generic{u} linux-backports-modules-2.6.28-16-generic{u}
The following packages will be upgraded:
  bind9-host dnsutils kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data khelpcenter4
  libbind9-40 libdns45 libisc45 libisccc40 libisccfg40 liblwres40 libplasma3
  linux-backports-modules-jaunty linux-backports-modules-jaunty-generic linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
26 packages upgraded, 6 newly installed, 2 to remove and 0 not upgraded.
Need to get 87.6MB of archives. After unpacking 185MB will be used.
Do you want to continue? [Y/n/?]
Would download/install/remove packages.
```

---

### Post by slakkie on 2009-12-12
There shouldn't be any problem performing that update.

---

### Post by sripplinger on 2009-12-13
So, running apt-get dist-upgrade will not install karmic, right?

---

### Post by slakkie on 2009-12-14
> **sripplinger said:**
> So, running apt-get dist-upgrade will not install karmic, right?

Hard to say without looking at your sources.list...

Could you run *apt-cache policy linux-backports-modules-2.6.28-17-generic*?

That should give me some information about where the package is coming from.

apt-get dist-upgrade/aptitude full-upgrade will not automaticly upgrade a machine to a newer release. You'll need to edit your sources.list for that to happen.

dist-upgrade/full-upgrade will remove packages in order to install newer packages. Have a look at the man-page of both apt-get and aptitude.

apt-get:
> 
       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of
           packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. So, dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains a list of locations
           from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual
           packages.


aptitude:
> 
       full-upgrade
           Upgrades installed packages to their most recent version, removing or installing packages as necessary. This command is less conservative
           than safe-upgrade and thus more likely to perform unwanted actions. However, it is capable of upgrading packages that safe-upgrade cannot
           upgrade.

           Additional <package>s listed on the command line are treated as extra actions to be taken above and beyond simply upgrading all packages.
           These arguments are treated in the same manner as arguments to aptitude install; for instance, aptitude dist-upgrade gimp- will upgrade all
           packages that can be upgraded, except for gimp, which will be removed.

               Note
               This command was originally named dist-upgrade for historical reasons, and aptitude still recognizes dist-upgrade as a synonym for
               full-upgrade.


---

