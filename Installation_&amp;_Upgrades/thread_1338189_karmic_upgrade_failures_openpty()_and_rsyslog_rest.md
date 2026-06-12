---
title: "karmic upgrade failures: openpty() and rsyslog restart failed"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by smaring on 2009-11-26
following what I thought would be a minor upgrade in Karmic my server is now inoperable.  Trying to open a terminal from gnome tells me "There was an error creating the child process for this terminal", but at least I can <ctl><alt> to another virtual console.

After manually reconfiguring my nic I tried an "apt-get -f install" and got ...

```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up rsyslog (4.2.0-2ubuntu5.1) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service rsyslog restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart rsyslog
restart: Unknown instance: 
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 rsyslog
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

My business is dead in the water at the moment and I have to start worrying about turkey soon.  So, ANY thoughts are most welcome!

Thanks,
Steve Maring

---

### Post by smaring on 2009-11-26
oops ... didn't notice that there was another dist-upgrade in queue right behind it ... that fixed it

---

