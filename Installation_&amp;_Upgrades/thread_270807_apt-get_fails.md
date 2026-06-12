---
title: "apt-get fails"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by JamesVeDe on 2006-10-03
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)


I've looked at the results returned from google... no dice on the 1 entry. Anybody with ideas?

---

### Post by JamesVeDe on 2006-10-03
PS All Synaptic installs fail with:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

---

