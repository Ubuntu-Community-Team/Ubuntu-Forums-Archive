---
title: "Problems with nagvis installation and configuration"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by nvinod on 2015-10-01
I have tried to install gvim and for some reason it started installing nagvis. While installing the nagvis (apparently it requires appache server), I forcefully aborted the installation.

From that point I am neither able to install new programs nor able to remove the existing ones.

I tried sudo dpkg --configure -a 
 ****************************************************************************************************************************************
Setting up nagvis (1:1.7.10+dfsg1-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package nagvis (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nagvis-demos:
 nagvis-demos depends on nagvis (= 1:1.7.10+dfsg1-2); however:
  Package nagvis is not configured yet.

dpkg: error processing package nagvis-demos (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nagvis
 nagvis-demos
************************************************************************************************

I do not want remove nagvis and would like to remove it completely. Looking for solutions and thanks in advance.

---

