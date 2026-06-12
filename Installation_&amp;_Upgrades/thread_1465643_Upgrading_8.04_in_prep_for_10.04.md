---
title: "Upgrading 8.04 in prep for 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by turb0chrg on 2010-04-29
Hi all.

Getting my 8.04 system ready to upgrade to 10.04 by doing all the upgrades but running into the following. It looks like the update-rc.d script it being passed bad arguments? Any help is really appreciated. Thanks!

```
$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  initscripts
The following partially installed packages will be configured:
  cron exim4 exim4-base exim4-daemon-light logrotate ntp
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up cron (3.0pl1-100ubuntu2.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of logrotate:
 logrotate depends on cron | anacron | fcron; however:
  Package cron is not configured yet.
  Package anacron is not installed.
  Package fcron is not installed.
dpkg: error processing logrotate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on cron | fcron; however:
  Package cron is not configured yet.
  Package fcron is not installed.
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
Setting up ntp (1:4.2.4p4+dfsg-3ubuntu2.3) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cron
 logrotate
 exim4-base
 exim4-daemon-light
 exim4
 ntp
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ntp (1:4.2.4p4+dfsg-3ubuntu2.3) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Setting up cron (3.0pl1-100ubuntu2.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on cron | fcron; however:
  Package cron is not configured yet.
  Package fcron is not installed.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of logrotate:
 logrotate depends on cron | anacron | fcron; however:
  Package cron is not configured yet.
  Package anacron is not installed.
  Package fcron is not installed.
dpkg: error processing logrotate (--configure):
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
Errors were encountered while processing:
 ntp
 cron
 exim4-base
 exim4-daemon-light
 logrotate
 exim4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

---

### Post by jjcv on 2010-04-30
Does the same thing happen when you run

aptitude safe-upgrade

again?

What does "apt-get -f install" show?

---

### Post by turb0chrg on 2010-04-30
Thanks !

apt-get safe-upgrade does the same again.

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cron (3.0pl1-100ubuntu2.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of logrotate:
 logrotate depends on cron | anacron | fcron; however:
  Package cron is not configured yet.
  Package anacron is not installed.
  Package fcron is not installed.
dpkg: error processing logrotate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on cron | fcron; however:
  Package cron is not configured yet.
  Package fcron is not installed.
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
Setting up ntp (1:4.2.4p4+dfsg-3ubuntu2.3) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cron
 logrotate
 exim4-base
 exim4-daemon-light
 exim4
 ntp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Looks like same error involving the update-rc.d script? Weird!

---

### Post by turb0chrg on 2010-05-03
Any suggestions for this one? Or if none, how do I back out of this mess and go back to where I was?

Thanks, Joel.

---

### Post by turb0chrg on 2010-05-30
Fixed this: [https://bugs.launchpad.net/ubuntu/+source/cron/+bug/354589](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/354589)

---

