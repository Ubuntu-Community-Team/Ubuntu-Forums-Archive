---
title: "Installing apache2. E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by mast3r67.gaby on 2013-12-10
I'm getting while installing apache2 (sudo apt-get install apache2):

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up apache2.2-common (2.2.22-13) ...
insserv: warning: script 'S99hello' missing LSB tags and overrides
insserv: warning: script 'S20ukbd' missing LSB tags and overrides
insserv: warning: script 'hello' missing LSB tags and overrides
insserv: warning: script 'ukbd' missing LSB tags and overrides
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Starting hello depends on stop-bootlogd and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: There is a loop between service stop-bootlogd and mountnfs if started
insserv:  loop involving service mountnfs at depth 9
insserv:  loop involving service nfs-common at depth 8
insserv:  loop involving service mpt-statusd at depth 10
insserv: There is a loop between service stop-bootlogd and mountall if started
insserv:  loop involving service mountall at depth 5
insserv:  loop involving service checkroot-bootclean at depth 4
insserv:  loop involving service mountnfs-bootclean at depth 11
insserv: There is a loop between service stop-bootlogd and urandom if started
insserv:  loop involving service urandom at depth 6
insserv:  loop involving service networking at depth 8
insserv:  loop involving service checkfs at depth 5
insserv:  loop involving service mountall-bootclean at depth 7
insserv:  loop involving service kbd at depth 12
insserv: There is a loop between service hello and udev if started
insserv:  loop involving service udev at depth 1
insserv:  loop involving service rsyslog at depth 13
insserv: There is a loop at service stop-bootlogd if started
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv: There is a loop at service hello if started
insserv:  loop involving service console-setup at depth 16
insserv:  loop involving service hello at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-worker:
 apache2-mpm-worker depends on apache2.2-common (= 2.2.22-13); however:
  Package apache2.2-common is not configured yet.


dpkg: error processing apache2-mpm-worker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (= 2.2.22-13) | apache2-mpm-prefork (= 2.2.22-13) | apache2-mpm-event (= 2.2.22-13) | apache2-mpm-itk (= 2.2.22-13); however:
  Package apache2-mpm-worker is not configured yet.
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is not installed.
 apache2 depends on apache2.2-common (= 2.2.22-13); however:
  Package apache2.2-common is not configured yet.


dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2.2-common
 apache2-mpm-worker
 apache2
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Any ideas?

---

