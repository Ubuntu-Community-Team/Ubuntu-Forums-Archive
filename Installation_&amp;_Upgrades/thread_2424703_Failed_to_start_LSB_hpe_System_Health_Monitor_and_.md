---
title: "Failed to start LSB: hpe System Health Monitor and Command line Utility Package.."
date: 2019-08-13
forum: Installation &amp; Upgrades
---

### Post by jyotiranjan32 on 2019-08-13
I am trying install a package through apt-get install and facing below issue.

> sudo apt-get install python
Reading package lists... Done
Building dependency tree
Reading state information... Done
python is already the newest version (2.7.15~rc1-1).
The following packages were automatically installed and are no longer required:
  lib32stdc++-4.8-dev libx32stdc++-4.8-dev
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 161 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up hp-health (10.80-1874.10) ...
Job for hp-health.service failed because the control process exited with error code.
See "systemctl status hp-health.service" and "journalctl -xe" for details.
invoke-rc.d: initscript hp-health, action "start" failed.
&#9679; hp-health.service - LSB: hpe System Health Monitor and Command line Utility Package.
   Loaded: loaded (/etc/init.d/hp-health; generated)
   Active: failed (Result: exit-code) since Tue 2019-08-13 09:48:27 UTC; 6ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2989 ExecStart=/etc/init.d/hp-health start (code=exited, status=1/FAILURE)


Aug 13 09:48:27 msabonham systemd[1]: Starting LSB: hpe System Health Monitor and Command line Utility Package....
Aug 13 09:48:27 msabonham hp-health[2989]:   Trying to identify the Product Name...
Aug 13 09:48:27 msabonham hp-health[2989]:   ERROR: This server is NOT supported!
Aug 13 09:48:27 msabonham hp-health[2989]:   Error: No supported management controller found
Aug 13 09:48:27 msabonham systemd[1]: hp-health.service: Control process exited, code=exited status=1
Aug 13 09:48:27 msabonham systemd[1]: hp-health.service: Failed with result 'exit-code'.
Aug 13 09:48:27 msabonham systemd[1]: [COLOR=#ff0000]Failed to start LSB: hpe System Health Monitor and Command line Utility Package..[/COLOR]
dpkg: error processing package hp-health (--configure):
 installed hp-health package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 hp-health
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anybody seen this error before.If so can anybody help me to stop the HPE health service .

---

