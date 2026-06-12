---
title: "the following packages have been kept back: landscape-common"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by zeefreak on 2010-09-18
i have a strange thing happening when i try to run apt-get upgrade. i'm able to upgrade anything i want, except landscape-common [whatever that is].

```
$ sudo apt-get update
.
.[output omitted, no errors]
.
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  landscape-common
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
```

the only other thread on here is from ages ago and the solution was to terminate a screen session that was running in the background. i have no screen sessions running, and actually just rebooted after a kernel upgrade, so there shouldn't be any background processes running at all.

---

### Post by elraun on 2010-09-20
you can either:

```
apt-get dist-upgrade
``` 

or remove the package if you don't need it.

i think it does this because a new package is required to update landscape but i'm not actually sure.

---

### Post by slakkie on 2010-09-20
> **elraun said:**
> you can either:

```
apt-get dist-upgrade
``` 

or remove the package if you don't need it.

i think it does this because a new package is required to update landscape but i'm not actually sure.


Then do apt-get -s dist-upgrade, it will simulate the command. Personally, I prefer aptitude:

```

sudo aptitude keep-all
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

```

You can also do to figure out why/what and who is dependent on landscape-common.

```

aptitude show landscape-common
# and 
apt-cache policy landscape-common
# and
aptitude search ~i ~Rlandscape-common
# or 
apt-cache rdepends landscape-common

```

---

### Post by zeefreak on 2010-09-20
i did some rummaging to find out what this is, and it looks like some kind of management tool for ubuntu, and something you have to pay for to boot. i never installed it, so really don't understand why its on there, much less why it's giving me problems. more oddly, its saying it wasn't automatically installed.

```
$ aptitude show landscape-common
Package: landscape-common
State: installed
Automatically installed: no
Version: 1.5.2.1-0ubuntu0.10.04.0
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,491k
Depends: python (< 2.7), python (>= 2.6), python-central (>= 0.6.11), debconf
         (>= 0.5) | debconf-2.0, libpam-modules (>= 1.0.1-9ubuntu3),
         python-smartpm (>= 1.2-4), python2.6-dbus, python-gnupginterface,
         python-twisted-core, python-gobject, python-apt, ca-certificates,
         perl-modules, python-gdbm, lsb-release, lsb-base, adduser
Suggests: python-image-store-proxy
Replaces: landscape-client (<= 1.0.23-0ubuntu0.8.10)
Description: The Landscape administration system client
 Landscape is a web-based tool for managing Ubuntu systems. This package is
 necessary if you want your machine to be managed in a Landscape account. 
 
 This package provides the core libraries.

$ apt-cache policy landscape-common
landscape-common:
  Installed: 1.5.2.1-0ubuntu0.10.04.0
  Candidate: 1.5.4-0ubuntu0.10.04.0
  Version table:
     1.5.4-0ubuntu0.10.04.0 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
 *** 1.5.2.1-0ubuntu0.10.04.0 0
        100 /var/lib/dpkg/status
     1.5.0.1-0ubuntu0.10.04.0 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
$ apt-cache rdepends landscape-common
landscape-common
Reverse Depends:
  landscape-client
  landscape-client

```

---

### Post by Sven6210 on 2011-04-09
I have had the same issue with the module 'landscape-common'. I did the following to finally solve it:

1. I run "aptitude show landscape-common" to see what the module is for. I showed me that I do not need this module for my use and that it depends on two old kernel header files (the kernel has already been updated)

2. I run "apt-get install" and it showmed me that these two old kernel header files are obsolete in the system

3. I run "apt-get autoremove" in order to remove these two header files

4. I run "aptitude remove landscape-common" in order to remove the "landscape-common" module that I have no use for.

After these steps the system was fine again and all packages were up to date.

---

