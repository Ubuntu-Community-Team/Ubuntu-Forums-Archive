---
title: "Something bad happened with last apt-get upgrade"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by ultralame on 2008-08-09
Last week I ran an update and it froze the system.  After trying to gracefully shutdown with Sysreq keys (maybe successful?) I have some problems...

```
$ cat /etc/issue
Ubuntu 8.04.1 \n \l

```

```
$ sudo dpkg --configure libglib2.0-0
Setting up libglib2.0-0 (2.16.4-0ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libglib2.0-0 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:

```

how do I deal with this?

This (and maybe a couple others) is blocking the installation of other packages.  In addition, some of my UI is messed up (probably due to broken dependencies on the aforementioned package).

---

