---
title: "Bug or I'm confused about updates."
date: 2014-06-26
forum: Installation &amp; Upgrades
---

### Post by papibe on 2014-06-26
Hi all,

There are several compiz and unity updates available at the 'trusty-updates' repository. These packages has been available in there at least a couple of days:
```
$ apt-cache policy compiz unity

compiz:
  Installed: 1:0.9.11+14.04.20140409-0ubuntu1
  Candidate: 1:0.9.11+14.04.20140423-0ubuntu1
  Version table:
     1:0.9.11+14.04.20140423-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 1:0.9.11+14.04.20140409-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

unity:
  Installed: 7.2.0+14.04.20140423-0ubuntu1.2
  Candidate: 7.2.1+14.04.20140513-0ubuntu2
  Version table:
     7.2.1+14.04.20140513-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 7.2.0+14.04.20140423-0ubuntu1.2 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     7.2.0+14.04.20140416-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```
'apt-get' sees them and offer to install it:
```
$ sudo apt-get upgrade

[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default libcompizconfig0
  libdecoration0 libunity-core-6.0-9 unity unity-services
  unity-settings-daemon
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,809 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue? [Y/n] 

```
However, 'Software Updater' does not see them (see attached pictures). Note that 'trusty-updates' is check as source of updates.

I'd appreciate any hint or explanation you can give me.
Regards.

---

### Post by bapoumba on 2014-06-27
That is called phased updates papibe :)

apt-get does not check for phased updates, so you get anything available.
Updates are delivered to 10% of users. If no bug reports are raised, they are gradually offered to the remaining users over the next few days. If bugs are raised, updates spreading is stopped for these packages.

Here are the current updates status : [http://people.canonical.com/~ubuntu-archive/phased-updates.html](http://people.canonical.com/~ubuntu-archive/phased-updates.html)

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

### Post by papibe on 2014-06-27
Holy Moly! :)

Thanks a lot bapoumba.

Kind Regards.

---

### Post by bapoumba on 2014-06-28
You are most welcome papibe :)
I got also confused when I first noticed (and thanks to John from the lubuntu mailing list for pointing me to phased updates).

---

