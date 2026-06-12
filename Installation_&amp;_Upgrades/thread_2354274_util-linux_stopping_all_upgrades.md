---
title: "util-linux stopping all upgrades"
date: 2017-03-01
forum: Installation &amp; Upgrades
---

### Post by Westley on 2017-03-01
Hi,

I'm running Ubuntu 16.04.1 LTS server, terminal mode only.

When I try to install security updates it always fails on the following:
```
Setting up util-linux (2.27.1-6ubuntu3.2) ...
insserv: warning: script 'K01mongo' missing LSB tags and overrides
insserv: Service mountdevsubfs has to be enabled to start service hwclock
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I've tried dpkg --configure util-linux

and get 
```
Setting up util-linux (2.27.1-6ubuntu3.2) ...
insserv: warning: script 'K01mongo' missing LSB tags and overrides
insserv: Service mountdevsubfs has to be enabled to start service hwclock
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux

```
Thanks,
Westley

---

### Post by ian-weisser on 2017-03-01
Fix your script /etc/init.d/mongo. If you don't use it, uninstall the package.

---

### Post by Westley on 2017-03-01
Ian,

Thanks for the response. It gave me enough to get everything where it should be and I think my system is fully operational again.

Westley

---

