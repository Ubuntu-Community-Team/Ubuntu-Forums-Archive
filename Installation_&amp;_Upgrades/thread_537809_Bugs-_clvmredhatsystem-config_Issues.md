---
title: "Bugs- clvm/redhat/system-config Issues"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by HedgeHog74 on 2007-08-29
Greetings,

Every time I install updates or upgrades, I get this error message in both the terminal (either from cvs or sudo apt-get update or install...) and in the gnome window (after installing updates):

> 
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)


How do I fix this?  Everything seems to install just fine though; should I report this as a bug?  Also, I can't seem to find the syslog anywhere, even doing searches.  Any idea where I can find it?

Computer specs:
> 
Ubuntu 7.04 (Up to date)
AMD K6-2 500MHz 3-D
Brand New FIC-2130 Mobo w/VIA chipsets
Award BIOS
448MB SDRAM DIMM (1x133MHz-256MB,1x100MHz-128MB,1x100MHz-64MB; BIOS allows for different DIMM speeds)
Linksys LNE 100 (10/100 Tbase)
PnP Generic Monitor, Keyboard, & Optical USB Mouse


Hope someone here in Ubuntuland can help so I can rid this annoying error messages away for good.

-David :D

---

