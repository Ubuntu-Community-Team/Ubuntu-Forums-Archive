---
title: "software centre has error"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by zabit-khan on 2014-07-30
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 228042 files and directories currently installed.) 
Preparing to unpack .../tor_0.2.4.20-1_amd64.deb ... 
Unpacking tor (0.2.4.20-1) ... 
dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.20-1_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for ureadahead (0.100.0-16) ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/tor_0.2.4.20-1_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of torchat: 
 torchat depends on tor (>= 0.2.1.30-1); however: 
  Package tor is not installed. 
 
dpkg: error processing package torchat (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of tor-geoipdb: 
 tor-geoipdb depends on tor (>= 0.2.4.20-1); however: 
  Package tor is not installed. 
 
dpkg: error processing package tor-geoipdb (--configure): 
 dependency problems - leaving unconfigured

pls help me in this situation

---

### Post by ian-weisser on 2014-07-30
The error seems quite straightforward and clear to me. 

> **zabit-khan said:**
> dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.20-1_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4 

Packages may not overwrite each other's files. It means the two packages irreconcilably conflict, and you -the admin- must choose between them. Only one may be installed at a time.

Since the 'tor' package is from the Ubuntu repositories, and is tested and supported software, while the 'tor-browser' package is from someplace else, I know which one I would choose.

Since 'tor-browser' is installed, and 'tor' is merely marked to try to install, how you remove one depends upon which one you choose. Let us know, and we can show you the proper sequence of Terminal commands to easily resolve it.

---

