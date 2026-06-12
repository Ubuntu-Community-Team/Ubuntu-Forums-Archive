---
title: "Failed to start procps (1:3.2.8-11ubuntu6.3)"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by vicky8 on 2014-02-21
Hi,

This bug is already reported and resolved too in other versions of Ubuntu, but I am facing this issue in release 1:3.2.8-11ubuntu6.3 !

The procps service fails to start whenever I try to install or upgrade.

The command I am using is: sudo apt-get upgrade
Which results in tonnes of errors snippet is as follows:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
53 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up procps (1:3.2.8-11ubuntu6.3) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1

... SNIP ...

```

Any suggestion, clues are most welcome!

Best Regards,
Vicky

---

### Post by kelfen on 2015-02-12
Hi Vicky,
I have the same problem, when i tried to upgrade my system i receive this error:

```

  procps
Authentication warning overridden.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main procps amd64 1:3.2.8-11ubuntu6.4 [233 kB]
Fetched 233 kB in 0s (390 kB/s)
Setting up procps (1:3.2.8-11ubuntu6.3) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ppp:
 ppp depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing ppp (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 procps
 udev
 mountall
 ppp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

But at the moment i not found any solutions

---

### Post by kelfen on 2015-02-12
Hi Vicky,
i found a workaraound to complete the install or upgrade, try to rename your procps.conf as
```

mv /etc/init/procps.conf /etc/init/procps.conf.old

```

---

