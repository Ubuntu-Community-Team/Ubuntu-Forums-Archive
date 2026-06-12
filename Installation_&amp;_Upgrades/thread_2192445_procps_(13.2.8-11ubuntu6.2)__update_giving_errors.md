---
title: "procps (1:3.2.8-11ubuntu6.2)  update giving errors"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2013-12-07
How does one get around the folowing problem?

installArchives() failed: Setting up procps (1:3.2.8-11ubuntu6.2) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 procps
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up procps (1:3.2.8-11ubuntu6.2) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1


John

---

### Post by cigtoxdoc on 2013-12-15
This problem has been solved.  The problem was that I had not upgraded to the latest version of the SpiderOak client software.

John

---

