---
title: "Installing multiple versions of PHP buy Bind9 is failing to start."
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by Antexter on 2014-09-16
Hi,

So overall story is I'm trying to install multiple versions of PHP on a server as supposedly plesk supports this now.

I'm trying to configure PHP 5.6.0 when it bombs out saying

```
configure: error: xml2-config not found. Please check your libxml2 installation.
```

To which I try and do the usual sudo apt-get install libxml2 which results in 

```
Setting up bind9 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
 * Starting domain name service... bind9                                 [fail] 
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This time I give it a shot at installing bind9 see if it'll try and fix it I end up getting the same error above

```
Setting up bind9 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
 * Starting domain name service... bind9                                 [fail] 
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried removing it but it requests me to remove alot of plesk packages which I'm rather worried about doing as i dont want it to screw up plesk.
```
  bind9 plesk-core plesk-l10n pp-sitebuilder psa psa-backup-manager
  psa-health-monitor psa-horde psa-imp psa-ingo psa-kronolith psa-libxml-proxy
  psa-mimp psa-mnemo psa-passwd psa-turba psa-updates psa-vhost psa-watchdog
```

Any help is really appreciated!

Thanks.

---

