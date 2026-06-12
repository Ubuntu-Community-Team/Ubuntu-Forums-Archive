---
title: "Server upgrade dapper -&gt; Edgy error (pdnsd and sasl2-bin)"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by haaglin on 2008-01-11
During an upgrade of my server from dapper to edgy, the upgrade stops with this error: 

> Setting up pdnsd (1.2.4par-0.1) ...
Starting proxy DNS server: pdnsd (failed).
invoke-rc.d: initscript pdnsd, action "start" failed.
dpkg: error processing pdnsd (--configure):
subprocess post-installation script returned error exit status 1
Setter opp sasl2-bin (2.1.19.dfsg1-0.2ubuntu3) ...
Starting SASL Authentication Daemon: (failed).
invoke-rc.d: initscript saslauthd, action "start" failed.
dpkg: error processing sasl2-bin (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pdnsd
 sasl2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Error from syslog: 
> 
pdnsd[11410]: Could not bind tcp socket: Cannot assign requested address
pdnsd[11410]: Could not bind to udp socket: Cannot assign requested address
pdnsd[11410]: tcp and udp initialization failed. Exiting.


i tried apt-get -f install, apt-get dist-upgrade and sudo dpkg --configure -a. none of them worked.

---

