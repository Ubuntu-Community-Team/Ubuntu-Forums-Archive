---
title: "Dpkg read error in ldconfig trigger after libc6 update"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by jstewmc on 2011-05-08
Hi guys,

I'm running a LAMP server on Ubuntu 8.04 Server. I haven't updated it in a while, and I figured I'd upgrade this weekend. And that's when the fun started...

After a couple of hours of going around and around with broken dependencies caused by libc6-dev, I uninstalled the package with Synaptic Package Manager.  I figured I'd just re-install it after the upgrade. (I vaguely remember quitting an update earlier in the year which I started by accident, and I figured that was causing problems.)

Anyway, now I keep getting the same "read error" over and over:

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   libdns35  libtimedate-perl  dpkg-dev  patch
The following extra packages will be installed:
  libc6  libc6-dev  libc6-i686  libmysqlclient15-dev  libmysqlclient15off  mysql-common  zlib1g-dev
Suggested packages:
  glibc-doc  manpages-dev  mysql-doc-5.0
The following new packages will be installed:
  libc6-dev zlib1g-dev
The following packages will be upgraded:
  libc6  libc6-i686  libmysqlclient15-dev  libmysqlclient15off  mysql-common
5 upgraded, 2 newly installed, 0 to remove and 153 not upgraded.
2 not fully installed or removed.
Need to get 0B/18.2MB of archives.
After this operation, 13.8MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages...
dpkg: read error in '/var/lib/dpkg/triggers/ldconfig': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```How do I fix this error?

* Google is no help. It's all PATH errors with dpkg and ldconfig.
* I tried the various configure/clean/fix options to no avail.
```

$ dpkg --configure -a          # prints second to last line ("dpkg: read error..." ) from above
$ sudo apt-get clean           # running apt-get install after prints same output as above
$ sudo apt-get upgrade -f    # same output as above
$ sudo apt-get install -f       # same output as above

```* When I manually run the trigger (or so I think), I get a segmentation fault.
```

$ sudo dpkg-trigger --by-package=libc6 --no-await --no-act  ldconfig
Segmentation fault

```So, I'm no power user, and I can usually get by, but this is above my head. Any ideas?

Thanks!

---

