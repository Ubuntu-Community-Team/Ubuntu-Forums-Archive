---
title: "apt-get stopped to work after interrupted apt-get"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by vikim on 2008-09-15
PC got power-down in the middle of 'apt-get install'.
Since then, I cannot get apt-get to work again. It refuses to install anything, with erros [1].
Tried:
dpkg --configure -a --force-all
apt-get -f install
apt-get update
Purged all exim4-related packages. Didn't help.

How do I fix this ?

Thanks
Viki

[1]
Errors revolve around exim4. It had errors in configuring,
I purged it with --force-all. Now after every install, I
get:

Setting up exim4-config (4.69-2) ...
Description: prints name of nonexistent temporary file
Usage: tmpfile 
Options and arguments: none

dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4:
 exim4 depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-daemon-custom; however:
  Package exim4-daemon-light is not configured yet.
  Package exim4-daemon-heavy is not installed.
  Package exim4-daemon-custom is not installed.
dpkg: error processing exim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rkhunter:
 rkhunter depends on exim4 | postfix | sendmail | mail-transport-agent; however:
  Package exim4 is not configured yet.
  Package postfix is not installed.
  Package sendmail is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing rkhunter (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
 rkhunter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

