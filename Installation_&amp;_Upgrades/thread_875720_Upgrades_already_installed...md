---
title: "Upgrades already installed..?"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by DirtyMonkey on 2008-07-31
I have recently upgraded my webserver to Ubuntu 8.04 Hardy Heron but am having some problems with apt-get/synaptics.
My upgrade froze but after following this thread I managed to get it running again. [http://ubuntuforums.org/showthread.php?t=865679]("http://ubuntuforums.org/showthread.php?t=865679")

The problem is currently with some Plesk upgrades that it falsely reports as available to upgrade to but they are already installed as outlined below.

How can I fix this so that apt-get/synaptics reports the correct info?

Thanks in advance, DM.

```
root@server001:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  drweb-qmail libapache2-mod-bw php5-ioncube-loader ppwse psa
  psa-autoinstaller psa-awstats-configurator psa-firewall psa-horde psa-imp
  psa-ingo psa-kronolith psa-mailman-configurator psa-manual-custom-skin-guide
  psa-mimp psa-mnemo psa-mod-fcgid-configurator psa-passwd psa-qmail-rblsmtpd
  psa-spamassassin psa-turba psa-updates psa-vpn psa-watchdog sb-publish
  sshterm
26 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/57.8MB of archives.
After this operation, 1364kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  psa psa-watchdog php5-ioncube-loader ppwse drweb-qmail libapache2-mod-bw
  psa-autoinstaller psa-awstats-configurator psa-firewall psa-horde psa-imp
  psa-ingo psa-kronolith psa-mailman-configurator psa-manual-custom-skin-guide
  psa-mimp psa-mnemo psa-mod-fcgid-configurator psa-passwd psa-qmail-rblsmtpd
  psa-spamassassin psa-turba psa-updates psa-vpn sb-publish sshterm
Install these packages without verification [y/N]? y
(Reading database ... 152479 files and directories currently installed.)
Preparing to replace psa 8.6.0-ubuntu7.10.build86080722.00 (using .../psa_8.6.0-                                              ubuntu8.04.build86080722.00_amd64.deb) ...


===> Checking for the necessary system accounts
 Checking for the system groups and users necessary for MySQL...
 Checking for the group 'mysql'...
 Group 'mysql' already exists

 Checking for the user 'mysql'...
 User 'mysql' already exists

 Checking for the system groups and users necessary for admin server...
 Checking for the group 'psaadm'...
 Group 'psaadm' already exists

 Checking for the user 'psaadm'...
 User 'psaadm' already exists

 Checking for the group 'psaserv'...
 Group 'psaserv' already exists

 Checking for the group 'psaserv'...
 Trying to add supplementary group 'psaserv' for user 'www-data'...  already the                                              re
 Checking for the group 'psaserv'...
 Trying to add supplementary group 'psaserv' for user 'psaftp'...  already there
 Checking for the group 'psaserv'...
 Trying to add supplementary group 'psaserv' for user 'psaadm'...  already there
 Checking for the group 'psacln'...
 Group 'psacln' already exists

 Checking for the system groups and users necessary for Apache...
 Checking for the group 'www-data'...
 Group 'www-data' already exists

 Checking for the user 'www-data'...
 User 'www-data' already exists

    Unable to upgrade. You have  8.6.0 version installed,
    but upgrader is incompatible with this version.
    To install new Plesk copy, please move '/opt/psa'
    to another place manually.
dpkg: error processing /var/cache/apt/archives/psa_8.6.0-ubuntu8.04.build8608072                                              2.00_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/psa_8.6.0-ubuntu8.04.build86080722.00_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server001:~#

```

---

### Post by DirtyMonkey on 2008-07-31
Parallels have just confirmed this as a bug with Plesk 8.6

[http://forum.swsoft.com/showthread.php?p=211218#post211218]("http://forum.swsoft.com/showthread.php?p=211218#post211218")

---

